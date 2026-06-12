---
title: "eyeD3 command integration in Nautilus Actions"
date: 2008-10-16
forum: Multimedia Software
---

### Post by teachmeifyoucan on 2008-10-16
Hi,

I would like to integrate the eyeD3 --remove-all command into Nautilus Actions. I have created a Nautilus Action with the following settings:

[Menu Item & Action]
Label: Remove tags
Tooltip: Use eyeD3 to remove ID3 tag(s) from MP3 file(s)
Path: eyeD3
Parameters: --remove-all

[Conditions]
Filenames: *.mp3
Match case: unchecked
Mimetypes: */*
Appears if selection contains: Only files
Appears if selection has multiple files or folders: checked

[Advanced Conditions]
Appears if scheme is in this list: file | Local files (checked)
(all others unchecked)



Unfortunately, it doesn't work. Here is a list of eyeD3 commands:
[http://eyed3.nicfit.net/](http://eyed3.nicfit.net/)


Thanks for your help!

---

### Post by teachmeifyoucan on 2008-10-22
Bump!

---

