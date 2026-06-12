---
title: "Ubuntu 9.10 - Help me to obtain 5.1 channel Audio"
date: 2009-12-20
forum: Multimedia Software
---

### Post by siva_s on 2009-12-20
HI, i have installed ubuntu 9.10 and it is working great without any issues. But i tried to play 5.1 audio, only two speakers were working. So help me to get **_5.1 Dolby output_**. My laptop is acer 5738G with realtek card. 

Give me the related links if you can. Thanks!!!:confused:

---

### Post by siva_s on 2009-12-21
No reply yet!!! :(

---

### Post by HappyFeet on 2009-12-21
See [this]("https://help.ubuntu.com/community/SurroundSound").

---

### Post by alexfish on 2009-12-21
Hi 

Have a look at the Screen shot Below

From the Software center or Synaptic Load Install The Following

I Also                            Recommend installing Xine  Its Easy To Configure 

After installing Reboot Then The Controls Will Be Available From The  " Sounds and Video Menu "

For Each Application Make Sure The Controls Are Not Muted 

 To Get Best Results ;Play Around With The Settings in bother the player and pulse

Also Check For Plugins Pulse requires In Synaptic Type " pulse " in the Search area

Check The Permissions In Groups and Users / Manage Groups / Pulse

---

### Post by Maheriano on 2009-12-21
Which kind of audio cable are you using? Optical? Coaxial? HDMI?

---

### Post by Melcar on 2009-12-21
If you're using PulseAudio, then that defaults to 2ch. output (last time I used it anyway).  Easy enough to change though; just edit your /etc/pulse/daemon.conf file.  Check your volume levels too with alsamixer; my rear speakers are always muted on a fresh install.

---

### Post by siva_s on 2009-12-21
Thanks for the detailed replies...

But before seeing these ideas unfortunately i tried to install realtek audio package from their site... it removed old drivers and failed to install the new one... so now no sound is coming out from the system. 
In sound **preference -> hardware** option it shows *no hardware *
and in** Output** it shows *dummy output*

so u guys pls help me to bring the old sound system (at least 2.1 sound) from my system

---

### Post by siva_s on 2009-12-21
[B]
@ Maheriano[/B]

there is no optical or hdmi output.... it is having 3 pins... from this i can get front left,right/rear left,right/subwoofer,central speaker

---

### Post by lenkiatleong on 2009-12-22
> **alexfish said:**
> Hi 

Have a look at the Screen shot Below

From the Software center or Synaptic Load Install The Following

I Also                            Recommend installing Xine  Its Easy To Configure 

After installing Reboot Then The Controls Will Be Available From The  " Sounds and Video Menu "

For Each Application Make Sure The Controls Are Not Muted 

 To Get Best Results ;Play Around With The Settings in bother the player and pulse

Also Check For Plugins Pulse requires In Synaptic Type " pulse " in the Search area

Check The Permissions In Groups and Users / Manage Groups / Pulse

Hi,
From your image file, i noticed that you are using 5.1 analog. Are you able to stream 5.1 (dolby/dts/pcm) to AV receiver using **_optical_** cable?

I'm using Ubuntu 9.10 (64bit), Intel DP35DP mobo, 8GB RAM, Q6600 CPU. As this mobo has optical output and this is the only way to bitstream dolby/dts 5.1, i tried to set/configure ubuntu 9.10 but still fail to get 5.1 sound. I could only get Stereo using optical cable. I know its Stereo coming from the optical cable as shown in my Marantz AV8003 display panel.

From sound preferences, i can set 5.1 analog but could not find 5.1 digital. There are only 2 digital options for me to choose, i.e., Digital Stereo Duplex and Digital Stereo output + Analog stereo input.

I am not sure if this is due to my mobo (DP35DP) limitation or simply 9.10 settings are not configured correctly. As my receiver could get stereo, therefore, i reckon that the mobo should be alright. Unless the mobo only supports max Stereo thru the optical.

Hope to get help from gurus here.

Cheers
Len

---

### Post by alexfish on 2009-12-22
Hi

Try Editing the file /etc/modprobe.d/sound with a text editor.

Code:

sudo  gedit /etc/modprobe.d/sound

options snd-hda-intel model=auto 
options snd slots=snd-hda-intel
# u1Nb.Fok4Y2QakF0:82801I (ICH9 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel


'''''''''''''''''''''''''''''''''''''

Also

from the terminal check these kernels  match

Code:

modinfo soundcore

then

Code:

uname -vr

---

### Post by Maheriano on 2009-12-22
> **siva_s said:**
> [B]
@ Maheriano[/B]

there is no optical or hdmi output.... it is having 3 pins... from this i can get front left,right/rear left,right/subwoofer,central speaker

You just answered your question. This won't allow you to get Dolby 5.1, you need a digital output, not those three ports. Your only hope is to get a USB digital output sound card.

---

### Post by lenkiatleong on 2009-12-22
> **alexfish said:**
> Hi

Try Editing the file /etc/modprobe.d/sound with a text editor.

Code:

sudo  gedit /etc/modprobe.d/sound

options snd-hda-intel model=auto 
options snd slots=snd-hda-intel
# u1Nb.Fok4Y2QakF0:82801I (ICH9 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel


'''''''''''''''''''''''''''''''''''''

Also

from the terminal check these kernels  match

Code:

modinfo soundcore

then

Code:

uname -vr

Hi,

Thanks for your response.

I created /etc/modprobe.d/sound file as per your instructions and restarted the PC. After restart, i checked the sound preference and still, i could not find any "Digital 5.1" option in the list.

Pls see the screenshots below:
Screenshot1 shows the sound preference and the movie i was playing showed dolby sound mode selected.
Screenshot2 shows that sound file being created.
Screenshot3 shows that modinfo and uname matches.

Hope to get more instructions from you.
Thanks.

Len

---

