# imagesv6

站群正文配图的图床。文章正文引用 jsdelivr CDN 回源本仓库：

```
https://cdn.jsdelivr.net/gh/zshipu/imagesv6/<YYYY-MM-DD>/<sha1前16位>.<ext>
```

## 为什么图片不放在发布仓库里

站点 `static/` 下的图片会被 Hugo 原样复制进 publishDir（即 `zshipu-index`），
每天几十篇、每篇十几张，全部永久留在发布仓库里——它只会单调变大，
而 GitHub Pages 拉的就是那个仓库，越大越慢，历史也无法回收。
图床独立成库，发布仓库因此只剩 HTML。

## 约定

- 目录按 `YYYY-MM-DD` 分片，与 imagesv3/v4/v5 布局一致
- 文件名取源 URL 的 sha1 前 16 位，因此同一张图重复出现只落一份、命名幂等
- `manifest.tsv` 记录「这张图原本在哪」，是迁移与回溯的唯一账本；
  它是本地工作文件，不进版本库（见 .gitignore）
