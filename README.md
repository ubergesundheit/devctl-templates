## Setup templates repo

clone devctl

```
git filter-repo $(find -name *.template | sed -e 's,^\./,--path ,' | tr '\n' ' ') --path-rename pkg/gen/input/: --filename-callback '
  if filename is None:
    return None
  if b"internal/file/" in filename:
    return filename.replace(b"internal/file/", b"")
  '
```

