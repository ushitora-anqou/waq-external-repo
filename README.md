# waq-external-repo

## ffmpeg

```
ls ocaml-ffmpeg/opam/*.opam | \
while read line; do
base=$(basename $line)
base=${base%.*}
dir=${base}/${base}.1.2.7+waq.1
mkdir -p ${dir}
cp $line ${dir}/opam
cat <<EOS >> ${dir}/opam
url {
  src: "https://github.com/ushitora-anqou/ocaml-ffmpeg/archive/refs/tags/1.2.7+waq.1.tar.gz"
  checksum: [
    "md5=2dc98d1396e9aa8a1979c4c622210837"
    "sha512=f1a9b55eb97a2951a72f31cb962fb45ce93dd2961d8b80bedd34c01e304061a9e5887f9409be05f57cacbe5a24fc18c32b7d639ae06b6190c1db9190c41ba76f"
  ]
}
EOS
sed -r -i 's/^version: "1.2.7"$/version: "1.2.7+waq.1"/' ${dir}/opam
done
```
