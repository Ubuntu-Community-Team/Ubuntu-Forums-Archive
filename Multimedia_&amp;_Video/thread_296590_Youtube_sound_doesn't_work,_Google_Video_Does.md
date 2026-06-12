---
title: "Youtube sound doesn't work, Google Video Does"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by Bastanteroma on 2006-11-09
A few days ago sound stopped working for me at Youtube but it still works at Google Video, both of which, as far as I know, use Flash.

I've tried editing /etc/firefox/firefoxrc to say FIREFOX_DSP="aoss", I've launched firefox using [aoss firefox], I tried installing libflash-mozplugin, I tried reverting to Flash 7, and I tried the following:

# Flash also looks for /usr/lib/libesd.so.1
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

# Flash expects /tmp/.esd/socket to exist.
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

I did and undid these things in various combinations, rebooting in between, and sound never stopped working in other programs.  I'm using Flash9, installed by automatix2.

Any ideas?

---

### Post by Mimsy on 2006-11-09
I have the same problem, and have tried the same solutions, and several others, including the ones in the tutorials my signature links to. Still no sound. :(

/Mimsy

---

### Post by phy5ik on 2006-11-10
I'm having the same problem except that I cannot get sound on google video OR youtube. Any help?

---

### Post by phy5ik on 2006-11-10
.

---

### Post by ampop on 2006-11-10
I have the same problem.

---

### Post by reyfer on 2006-11-10
That is strange, I have Firefox 2 running Flash 9 too, but I have no problems whatsoever with Youtube or GoogleVideo or Veoh or any other flash site :confused:

---

### Post by norwyn on 2006-11-21
Doesn't work for me either.
Neither google video or youtube

---

### Post by Pete051 on 2006-11-21
My problem is similar sound and video work on mytube but only sound on myspace it's got me baffled :)

---

### Post by Pete051 on 2006-11-21
Hmm I see I've been a bit lacking in details there, it's Firefox 2 on edgy kubuntu

---

### Post by ciscosurfer on 2006-11-21
Flash 9 beta 2 has been released and supposedly takes care of the audio/crashing issues with FF -- we'll see.  

Here's the link: [http://blogs.adobe.com/penguin.swf/2006/11/beta_ii_the_audio_fix.html](http://blogs.adobe.com/penguin.swf/2006/11/beta_ii_the_audio_fix.html)

---

### Post by celem on 2006-11-21
> **ciscosurfer said:**
> Flash 9 beta 2 has been released and supposedly takes care of the audio/crashing issues with FF -- we'll see.  

Here's the link: [http://blogs.adobe.com/penguin.swf/2006/11/beta_ii_the_audio_fix.html](http://blogs.adobe.com/penguin.swf/2006/11/beta_ii_the_audio_fix.html)

:) 
I installed this update and it fixed the problem. Youtube now plays fine including the sound.

---

### Post by ampop on 2006-11-22
It works with me too. Thank you very much.

---

### Post by iceportal on 2008-06-22
Will this work for FF3?

I'm on default Ubuntu 8.04 install, up to date, with FF3.

---

