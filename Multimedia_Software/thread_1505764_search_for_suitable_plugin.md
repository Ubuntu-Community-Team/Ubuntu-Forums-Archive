---
title: "search for suitable plugin?"
date: 2010-06-09
forum: Multimedia Software
---

### Post by geyids on 2010-06-09
Hi Forums, My totem does not play internet radio nor internet tv. I bet its the mmsh codec thats missing. This is the message I get.

Any idea how to work out this? It used to work in my Jaunty now doesnt work in my Karmic

```
The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.
```

A link will be appreciated too

---

### Post by no2498 on 2010-06-09
just a ? you do this yet

sudo apt-get install ubuntu-restricted-extras


hope that helps

---

### Post by geyids on 2010-06-09
mmmm thanks. let me try that out. I really had not thought of that

---

### Post by Yellow Pasque on 2010-06-10
Yeah, the mms plugin is in gstreamer0.10-plugins-bad package.

---

### Post by geyids on 2010-06-10
How come I cant play any channel from [http://www.free-internet-tv.org/news/FTV-main.htm](http://www.free-internet-tv.org/news/FTV-main.htm) using totem? Does it work for anyone else out there?

---

### Post by belkinsa on 2010-06-26
Okay, I must bump this also.  I can't play anything from any Internet radio site just on their site.  I have the plug-ins but no playback or whatever it is called.  Oh, I have 10.04, but this was happening to me when I had 9.10 also.

The screen-shot shows a page, couldn't that help?

---

### Post by geyids on 2010-06-27
Mine still doesn't work too but I had it working fine in ubuntu 9.04. I didnt use ubuntu 9.10

---

### Post by samijildeh on 2010-06-27
i have ubuntu 10.04 and i can watch internet TV with totem.
i have ubuntu-restricted-extras.

---

### Post by samijildeh on 2010-06-27
watching - [http://www.free-internet-tv.org/news/FTV-main.htm](http://www.free-internet-tv.org/news/FTV-main.htm) - by totem, works for me.

---

### Post by geyids on 2010-06-27
Hey samijildeh which station are you watching so I can try with the same?

---

### Post by belkinsa on 2010-06-27
Deleted.

---

### Post by belkinsa on 2010-06-29
Alright, I think I have the solution.  I was chatting on the Ubuntu channel via IRC and one person told me a very good solution.  It's play the stream file with totem (the app) not the browser's app.  The person said this to me in a PM (I'm belkinsa):

> 
belkinsa: Did you try opening the stream in totem proper rather than the brower plugin? The automagic codec installation doesn
belkinsa: ... doesn't work with the browser plugin.


Thank you Jordan_U for this.

P.S. Also, I learned from Oer, another person from chatting on the channel, that it's a bug on Linux and Apple.  And he said that just find the .mpu or whatever they are called and use them with your player of choice.

Thank you Oer for that also.

I hope that helps everyone.

---

### Post by belkinsa on 2010-06-29
Okay, this solution doesn't work for me.  I have also looked up how to get that codec and nothing worked for me.  If it (the one above) works for anyone, please tell what you have done.  Thanks.

---

### Post by geyids on 2010-06-30
Hi Mechafish

I think most of the internet links are broken. Some cant play in other players like VLC too. Try this link as it is working for me here : [3ABN]("http://www.3abntv.org/player_old.cfm"). If it doesnt work for you, maybe your computer has a problem :)

---

### Post by belkinsa on 2010-07-01
You know what?  I think it's my computer.

---

### Post by geyids on 2010-07-01
:)

---

### Post by belkinsa on 2010-07-09
> **Mechafish said:**
> You know what?  I think it's my computer.

AND it's my computer.  Now, I'm wondering if I can fix it or...  never mind.

---

