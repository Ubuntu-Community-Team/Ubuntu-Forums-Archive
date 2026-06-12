---
title: "How to assing .m3u link in Firefox to open in Audacious?"
date: 2009-06-14
forum: Multimedia Software
---

### Post by orbital on 2009-06-14
Everytime I click on .m3u link, Firefox starts playing the stream with some plugin. How can I assign this .m3u link to automatically open in Audacious?

---

### Post by briguy47 on 2009-06-14
> **orbital said:**
> Everytime I click on .m3u link, Firefox starts playing the stream with some plugin. How can I assign this .m3u link to automatically open in Audacious?


I looked into this, and there doesn't seem to be an easy answer.  I do think the following will work though.


1. Open your favorite terminal and cd into your Firefox configuration directory:

```
cd ~/.mozilla/firefox/*.default
```
2. Open the MimeType config file:

```
gedit mimeTypes.rdf
```
3. Press Ctrl+F and search for:

```
<NC:fileExtensions>mp3</NC:fileExtensions>
```
4. Insert a new line just above that line and type:

```
<NC:fileExtensions>m3u</NC:fileExtensions>
```5. Save the file and restart firefox.


This should cause Firefox to open m3u files with whatever program you have specified for mp3 files under the Applications tab of the Preferences dialog.

Hope that helps.  Let me know if you need any more help!  :D

---

### Post by orbital on 2009-06-14
Thanks for the help,

It seems like it didn't help, but I changed the default action for streamed MP3 to "Open with Audacious" and now it seems to work, thanks a lot

---

