---
title: "ffmpeg need total help"
date: 2008-06-30
forum: Multimedia Software
---

### Post by mraiur on 2008-06-30
Hi. 


I need to know what exactly to do to install and use to convert movie clips whit ffmpeg, i convert movies but there is no output audio ...

---

### Post by aquavitae on 2008-06-30
Are you trying to convert movies from one format to another? Try installing avidemux, its got a nice and easy gui. I wouldn't use ffmpeg by itself (I'm not even sure if you can without programming something).  If you want something you can use from the command line try mencoder or transcode.

---

### Post by mraiur on 2008-06-30
The problem is that i can only use terminal ... i mean i installed Ubuntu Desktop but i only can excess it true the console ... and mencoder converts fine but i cant use it eater .... only ffmpeg .

I need to convert avi,mp4,mpeg to .flv format

---

### Post by aquavitae on 2008-06-30
Why can you only use the terminal - are you having problems getting the gui working? Also, why can't you use mencoder? I'd suggest you get thoses issues sorted out (If they are issues), but if you really need to use ffmpeg, have you tried checking the man page for usage: ```
man ffmpeg
```There are quite a lot of optional arguments for it which are listed there.

---

### Post by mraiur on 2008-06-30
They are not issues but the site i need make flv videos dont accept mancoder converted files . And i need to know how to make convertions true the console becouse i will reinstall the machine and install ubuntu server ... :D

---

### Post by aquavitae on 2008-06-30
Ok, so you want to know how to do it through the console because you don't want to rely on a gui - fair enough :). I don't know why the site wouldn't accept mencoder encrypted files though... How does it know? And what error does it give? Did you check the man page for help on ffmpeg?

---

### Post by mraiur on 2008-06-30
The site specificaly i need the movies is [http://vbox7.com](http://vbox7.com) its a bulgarian youtube ecvivalent it sux but i have several movies of friends that i need to upload and the stuped site refuses to convert the .mp4 clips .... and i converted them with ffmpeg and it uploaded them but when i watched them they have no sound .... i converted them with mencoder and there where no problems but the site refused them i can convert them under XP with flash video converter but i need to know how to do it with ffmpeg under ubuntu cuz no normal person will make a server under Windows ... :D

---

### Post by gandaran on 2008-06-30
mraiur,
      use **winff** [http://www.winff.org/](http://www.winff.org/) a front-end gui for ffmpeg, no need to use the terminal!, just make sure you install the medibuntu repository ffmpeg version.

edit: sorry I just read your post about not being able to use a gui.

---

### Post by aquavitae on 2008-07-01
I don't know much about the flv format, but does it have a specific sound codec associated with it? It could be that you've converted the video to flv, but the audio is still mp4. In that case have a look at the ffmpeg options again - there should be something about converting the sound. Actually I have a feeling that ffmpeg only converts video and you need something else to convert audio - Have you tried transcode? IIRC it uses ffmpeg to conver the video, but also handles the audio. And what did the site return when you tried uploading the mencoder encoded files?

---

### Post by eye208 on 2008-07-01
> **mraiur said:**
> I need to convert avi,mp4,mpeg to .flv format
Encoding FLV for YouTube with MEncoder:
```
mencoder yourmovie.xyz -srate 22050 -vf expand=:::::4/3,scale=320:240,harddup -af resample=22050 -ovc lavc -oac mp3lame -of lavf -lavcopts vcodec=flv:vbitrate=300 -lameopts cbr:br=64 -lavfopts format=flv -mc 0 -noskip -o yourmovie.flv
```
Wow, that was easy! ;)

Adjust the bitrate parameters as needed.

---

### Post by aquavitae on 2008-07-01
I love the simplicity of terminal commands ;)

---

### Post by mraiur on 2008-07-01
Thanks that work perfectly :)

---

