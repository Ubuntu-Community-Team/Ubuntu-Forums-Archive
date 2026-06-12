---
title: "albumart-qt can not fetch covers"
date: 2011-10-13
forum: Multimedia Software
---

### Post by e-San on 2011-10-13
Hi!

I am trying to download cover arts with albumart-qt.:

```
san@eeepc:/media/MARTA/Muzyka$ albumart-qt -d -i ./
Traceback (most recent call last):
  File "/usr/lib/albumart/albumart.py", line 118, in getAvailableCovers
    results += s.findAlbum("%s" % (artist), "%s" % (album))
  File "/usr/lib/albumart/albumart_source_amazon.py", line 52, in findAlbum
    return amazon.searchByKeyword(artist,album)
  File "/usr/lib/albumart/amazon.py", line 261, in searchByKeyword
    return search(artist, album, license_key, http_proxy, locale, associate)
  File "/usr/lib/albumart/amazon.py", line 243, in search
    url = buildURL(artist, album, license_key, locale)
  File "/usr/lib/albumart/amazon.py", line 219, in buildURL
    url += "&Keywords=%s" % (urllib.quote(album))
  File "/usr/lib/python2.7/urllib.py", line 1238, in quote
    return ''.join(map(quoter, s))
KeyError: u'\u0119'
Downloading cover images was interrupted by the following exception:
Traceback (most recent call last):
  File "/usr/lib/albumart/process.py", line 130, in run
    for cover in albumart.getAvailableCovers(artist, album, requireExactMatch = self.requireExactMatch):
  File "/usr/lib/albumart/albumart.py", line 118, in getAvailableCovers
    results += s.findAlbum("%s" % (artist), "%s" % (album))
  File "/usr/lib/albumart/albumart_source_amazon.py", line 52, in findAlbum
    return amazon.searchByKeyword(artist,album)
  File "/usr/lib/albumart/amazon.py", line 261, in searchByKeyword
    return search(artist, album, license_key, http_proxy, locale, associate)
  File "/usr/lib/albumart/amazon.py", line 243, in search
    url = buildURL(artist, album, license_key, locale)
  File "/usr/lib/albumart/amazon.py", line 219, in buildURL
    url += "&Keywords=%s" % (urllib.quote(album))
  File "/usr/lib/python2.7/urllib.py", line 1238, in quote
    return ''.join(map(quoter, s))
KeyError: u'\u0119'

Out of a total of 1676 items, 649 were recognized, 0 matching covers were found and 0 were installed.

```

no idea howto fix it...

Regards!

---

