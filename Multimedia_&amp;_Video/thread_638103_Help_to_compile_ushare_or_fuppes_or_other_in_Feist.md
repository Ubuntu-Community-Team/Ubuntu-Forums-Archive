---
title: "Help to compile ushare or fuppes or other in Feisty"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by blueorder on 2007-12-11
I have been trying to get either fuppes or ushare to work on my installation of Feisty so I can share avi's with my Xbox 360 but I am running into issues with dependencies.

Has anyone been able to compile/install either of these (or had success with another open source/free package) in Feisty and would be able to share how to compile or install?

I'm somewhat recent to Ubuntu but can do some things in cli. This one is just a bit more advanced than I can handle.

If you can provide detailed steps that would be greatly appreciated.

Also, if this helps, I'm trying to share the videos without the need to transcode (since the new dashboard update went out providing the ability to play avi)

Thanks,

---

### Post by Tadhg on 2007-12-12
there seem to be some problems with ffmpeg/transcoding and the latest fuppes release. 

UShare should compile no problem though, but for some reason my xbox won't play anything I share with UShare, even with the new update.

open a terminal and type:

sudo gedit /etc/apt/sources.list (This includes the repositories you have listed)

add "deb [http://www.geexbox.org/debian/](http://www.geexbox.org/debian/) unstable main" to the end of the file

save and close and type in the terminal

"sudo apt-get update && sudo apt-get install ushare"

that should install ushare for you

if you are having dependency problems, try type

"sudo apt-get -f install" and it will try install any outstanding dependancies

---

### Post by blueorder on 2007-12-12
> **Tadhg said:**
> there seem to be some problems with ffmpeg/transcoding and the latest fuppes release. 

UShare should compile no problem though, but for some reason my xbox won't play anything I share with UShare, even with the new update.

open a terminal and type:

sudo gedit /etc/apt/sources.list (This includes the repositories you have listed)

add "deb [http://www.geexbox.org/debian/](http://www.geexbox.org/debian/) unstable main" to the end of the file

save and close and type in the terminal

"sudo apt-get update && sudo apt-get install ushare"

that should install ushare for you

if you are having dependency problems, try type

"sudo apt-get -f install" and it will try install any outstanding dependancies

Thanks for your reply.

I tried to install using their repo last night but had broken packages/dependencies issues also.

I had the same error as [this person]("http://ubuntuforums.org/showpost.php?p=3935404&postcount=91"). My reply is [here]("http://ubuntuforums.org/showpost.php?p=3935435&postcount=92").

I was able to compile fuppes with the ```
--disable-transcoding
``` tag and was running. Some segfaults and when the xbox 360 saw the computer no files where there. I'm going to try to mess with fuppes a little after work and report back.

---

