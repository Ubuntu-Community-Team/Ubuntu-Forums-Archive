---
title: "no sound! help"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by cotin on 2008-02-20
Hey. I've just installed Ubuntu 7.10 and the only problem i have is to get the sound working. 
I use a latop;  HP pavillion dv9575. The laptop contains 3D Sound Blaster Pro-compitable sound. I have tried for a longtime to get the sound working. but no luck. So now im asking for your help.

---

### Post by cotin on 2008-02-21
help anyone???

---

### Post by sonrock3 on 2008-02-21
Try
1)
New user
= worked for me (stopped Sound Recorder startup error and failing to open)

2)
In user without sound:
Adjust sound settings, especially volumes, via Sound Control launcher near clock (screen top right).  I think it's called that.  I'm not in UB at the moment.
= I discovered here how to loose sound output (which I guess is your problem)

3)
Other user suggests at commmand line try alsamixer.
This opened a graphic of volume settings for me, that I could adjust using keybd navigation arrows - BUT it didn't fix my sound.

Good luck from
Stephen
New UB user,
proficient PC user (especially problem solving),
but NOT  developer / programmer.

---

### Post by FastZ on 2008-02-21
I helped fix a very similar problem on a friend's Pavilion 9000 series notebook, which had about the same specs as you stated yours has.  What I did to fix that problem was manually compile the Alsa drivers and after a reboot, sound worked perfectly.  You may want to try doing that and see what the outcome is in your situation.  

From what I've heard, the no sound problem is common with the HP 9000 series and Gutsy.  You'll get it fixed, don't worry.

Follow these instructions:

Step 1:
download this file to your desktop
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)

Step 2: 
in a terminal window type the following commands, one line at a time

```

cd Desktop
tar -xvf alsa-driver-1.0.16.tar.bz2
cd alsa*
./configure
make
sudo make install

```

---

### Post by cotin on 2008-02-22
Thank you very very much for your reply! I will try that right away

---

### Post by cotin on 2008-02-22
Everything goes wrong after 

./configure               

charlie@charlie:~/Desktop/alsa-driver-1.0.16$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
charlie@charlie:~/Desktop/alsa-driver-1.0.16$

need help

---

### Post by cotin on 2008-02-25
Heeelp Mee :(

---

### Post by superprash2003 on 2008-02-25
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by cotin on 2008-02-25
ok i will do it now..

---

### Post by cotin on 2008-02-25
sorry this didn't work.. i have alreaddy tried this..

---

### Post by cotin on 2008-02-25
> **FastZ said:**
> I helped fix a very similar problem on a friend's Pavilion 9000 series notebook, which had about the same specs as you stated yours has.  What I did to fix that problem was manually compile the Alsa drivers and after a reboot, sound worked perfectly.  You may want to try doing that and see what the outcome is in your situation.  

From what I've heard, the no sound problem is common with the HP 9000 series and Gutsy.  You'll get it fixed, don't worry.

Follow these instructions:

Step 1:
download this file to your desktop
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)

Step 2: 
in a terminal window type the following commands, one line at a time

```

cd Desktop
tar -xvf alsa-driver-1.0.16.tar.bz2
cd alsa*
./configure
make
sudo make install

```

Help

---

### Post by FastZ on 2008-02-26
> **cotin said:**
> Everything goes wrong after 

./configure               

charlie@charlie:~/Desktop/alsa-driver-1.0.16$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
charlie@charlie:~/Desktop/alsa-driver-1.0.16$

need help

Oh man, I'm so sorry for not getting back on here sooner.  Did you get this fixed yet?  Please accept my apologies for slacking on checking up in here.

I think what might be your problem here is that you need to install the build-essentials package.  Do so by typing the following in a terminal window.

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential

```

then try the original instructions for manually compiling the alsa driver.

Let me know if you get this fixed.

---

