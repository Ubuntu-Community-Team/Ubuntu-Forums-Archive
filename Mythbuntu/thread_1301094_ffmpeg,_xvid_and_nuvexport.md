---
title: "ffmpeg, xvid and nuvexport"
date: 2009-10-25
forum: Mythbuntu
---

### Post by GuiGuy on 2009-10-25
Is there a reasonably simple way to get ffmpeg to do xvid etc with nuvexport? 

I've tried to follow [these instructions]("http://ubuntuforums.org/showthread.php?t=1279156") but although it compiles it still won't do xvid. 

Thanks.

---

### Post by andyfrizzle on 2009-11-03
I personally don't use ffmpeg. (due to previous inconsistencies) 

I install Nuvexport using apt-get from the normal repositories.

I use the mencoder option for transcoding recordings to Xvid and it seems to work perfectly for me.

See the thread [_here_]("http://ubuntuforums.org/showthread.php?t=346778") for more information and details of transcoding options.

---

### Post by klc5555 on 2009-11-03
> **andyfrizzle said:**
> I personally don't use ffmpeg. (due to previous inconsistencies) 

I install Nuvexport using apt-get from the normal repositories.

I use the mencoder option for transcoding recordings to Xvid and it seems to work perfectly for me.

See the thread [_here_]("http://ubuntuforums.org/showthread.php?t=346778") for more information and details of transcoding options.

The --transcode option also works for xvid and generally gives better results than ffmpeg (particularly using the single-pass, higher quality command options), but is slower. (See the nuvexport wiki page at the mythtv wiki.)

If nuvexport (with or without a home-compiled ffmpeg) is bailing out, the cause is frequently a missing support library for ffmpeg (regardless of the nearly useless "svn-version" nuvexport/ffmpeg error message). Sometimes just issuing the command "ffmpeg" at a command prompt will indicate what that missing library is, or what the first missing library is, if there are several, so that the library can be added.

---

### Post by GuiGuy on 2009-11-03
> **klc5555 said:**
> The --transcode option also works for xvid and generally gives better results than ffmpeg (particularly using the single-pass, 

--transcode gives me the same immediate exit error on --xvid as ffmpeg. 


> 
If nuvexport (with or without a home-compiled ffmpeg) is bailing out, the cause is frequently a missing support library for ffmpeg (regardless of the nearly useless "svn-version" nuvexport/ffmpeg error message). Sometimes just issuing the command "ffmpeg" at a command prompt will indicate what that missing library is, or what the first missing library is, if there are several, so that the library can be added.

I had already exhausted all of those options prior to coming here.

The issue for me is that I have a rapidly filling HDD and no way to archive. I'm going to reinstall everything from new this weekend.If I cannot get it to work I do think it is time to face reality(see my signature line)

---

### Post by GuiGuy on 2009-11-03
> **andyfrizzle said:**
> I personally don't use ffmpeg. (due to previous inconsistencies) 

I install Nuvexport using apt-get from the normal repositories.

I use the mencoder option for transcoding recordings to Xvid and it seems to work perfectly for me.

It's good to hear it works for some. It used to work perfectly form me in 9.04 as well. 

> 
See the thread [_here_]("http://ubuntuforums.org/showthread.php?t=346778") for more information and details of transcoding options.

I make a habit of exhausting all the solutions and suggestions I can find on the 'net before posting here. The link above was among them. I would point out that it is a fairly old post and much of it's advice is redundant.

---

### Post by blackoper on 2009-11-12
I installed nuvexport from scratch last week and it was able to transcode mpeg 2 hd to mkv just fine. I had to do some trial and error and read the logs to narrow things down

---

### Post by fimbar on 2009-12-01
> **blackoper said:**
> I installed nuvexport from scratch last week and it was able to transcode mpeg 2 hd to mkv just fine. I had to do some trial and error and read the logs to narrow things down

Care to give some pointers as to how you achieved that, please?

nuvexport keeps returning a "**removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work**." error which I've googled and it seems the version of nuvexport in the repositories (0.21) under Karmic is incompatible with MythTV (which is 0.22)

---

### Post by blackoper on 2009-12-01
I switched over completely to mythnuv2mkv and havn't had any problems with the conversions since then. it has an xvid option in it.

Follow the directs on this page to get it working: [http://web.aanet.com.au/~auric/?q=node/6]("http://web.aanet.com.au/~auric/?q=node/6") and [http://www.mythtv.org/wiki/Mythnuv2mkv]("http://www.mythtv.org/wiki/Mythnuv2mkv")

It usually gives me an error in the myth job queue but completes fine.

---

### Post by fimbar on 2009-12-02
> **blackoper said:**
> I switched over completely to mythnuv2mkv and havn't had any problems with the conversions since then. it has an xvid option in it.
 
Follow the directs on this page to get it working: [http://web.aanet.com.au/~auric/?q=node/6](http://web.aanet.com.au/~auric/?q=node/6) and [http://www.mythtv.org/wiki/Mythnuv2mkv](http://www.mythtv.org/wiki/Mythnuv2mkv)
 
It usually gives me an error in the myth job queue but completes fine.
 
Thank you, I'll take a look at those links. Not heard of mythnuv2mkv before :)

---

