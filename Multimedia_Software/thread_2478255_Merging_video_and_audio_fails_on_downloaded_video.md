---
title: "Merging video and audio fails on downloaded video"
date: 2022-08-21
forum: Multimedia Software
---

### Post by py-ohayo on 2022-08-21
Hello,

I've discovered strange phenomena while trying to download videos from [https://revoir.tv5monde.com/](https://revoir.tv5monde.com/)
While videos are played normally on the site, once downloaded (e.g. using **yt-dlp**), only first 2min 39 sec are played with audio.
I tried to download video and audio separately and then merge them with **ffmpeg**, but the result is the same !

Here is a link I just tried:
[https://revoir.tv5monde.com/toutes-les-videos/documentaires/madame-le-general-une-femme-d-exception-madame-le-general](https://revoir.tv5monde.com/toutes-les-videos/documentaires/madame-le-general-une-femme-d-exception-madame-le-general)

The separately downloaded video and audio are [COLOR=#0000cd]814.5MB[/COLOR] and [COLOR=#0000cd]99.2MB[/COLOR] respectively.
But the resulting merge file (using **ffmpeg**) is the same size as the one produced by **yt-dlp**: [COLOR=#0000cd]819.7MB[/COLOR].
Any comments ?
Thanks.

---

