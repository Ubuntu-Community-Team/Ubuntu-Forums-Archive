---
title: "Getting 5.1 Surround Sound to work in 11.10"
date: 2011-10-17
forum: Multimedia Software
---

### Post by alsmith on 2011-10-17
Hi folks.

I'm currently setting up a desktop bought by my brother for using 11.10 on. He has a **5.1 Surround Sound** speaker setup. The motherboard has 5.1 surround sound as part of its onboard soundcard.

However, he only has three jacks at the back (Mic / Out / Line). Apparently we can configure these three jacks to output 5.1?

How can this be done?

Many thanks.


Al.

---

### Post by jpbn on 2011-10-22
[B][SIZE=2]hey, I spoke to a guy on launchpad:(actionparsnip (andrew-woodhead666) 
 and he suggested I go to this link 
 [http://www.webupd8.org/2009/06/enable-surround-sound-in-ubuntu-linux.html](http://www.webupd8.org/2009/06/enable-surround-sound-in-ubuntu-linux.html)
  if you go there it tells you to open the terminal and type alsamixer  and then you will see all your speakers... make sure they are not muted  and then use the right arrow on your keyboard and go right till you see a  channel option... it will be default at 2... change this to 6 if you  have 5.1 surround sound.... and then it will work... I believe this will  work after I restart my pc... I have not tested this yet... but so far  it works very good... sound comes from all my 6 speakers... videos and  music :) Hope this solves your problem[/SIZE][/B]

---

### Post by dazer26 on 2011-10-29
Go to your package manager (you might have to install synaptic, I dunno I use Kubuntu) and search pulse. Install paman, pavucontrol and pavumeter. After they are installed go to PulseAudio Volume Control under Multimedia. On the last tab (configuration) select you speaker setup (I use Analog Surround 7.1 output). It should work without having to restart, and now you can adjust the levels of the speakers under the Output Devices tab. 

The sound settings in Ubuntu (or Gnome/KDE?) are ****, I've had to install that pulse volume control in the last 3 releases to get surround working properly.

That link that everyone gives is ancient (you shouldn't have to open up a terminal anymore) and didn't solve the problem completely even when jaunty was still around.

---

### Post by pawelkoszalin on 2012-02-28
**@dazer26:**
Open a terminal and type:
```
gksu gedit /etc/pulse/daemon.conf
```Uncomment and change the following lines:
```
resample-method = speex-float-3
enable-remixing = yes
enable-lfe-remixing = yes

default-sample-rate = 48000
default-sample-channels = 6
default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
```Install PulseAudio Manager (paman). Also install pavucontrol and pavumeter.

Reboot your machine.

Open a terminal and type: pavucontrol
Go to "output devices" tab and set Subwoofer/LFE to 120% if you like deeper bass. :)

Works fine for me.

Sorry for my english...

---

### Post by Silviugdr on 2012-03-02
hello..i`m on ubuntu 11.10 x64, i`m using a 5.1 system and i don`t have  bass coming from the subwoofer when playing stereo music, when playing  music in 6 channels the subwoofer works but barely(low bass). at the  sound settings evrything looks ok, i`ve selected 5.1 output, the test  comes out ok. in alsamixer i`ve turned the subwoofer and LFE volume to  max, and still i get weak or not at all bass from the subwoofer. The  weird part is, if i play a music in banshee(or any other music player),  during the play, i change the settings from analog 5.1 output to any  other analog output setings, the bass blows off really loud like it  should, and if a change it back to analog 5.1 output it remains ok, with  bass..but this is only during the song. when i close or change the song  it`s back again with no bass, really crappy sound. i don`t know what to  do:sad:..and  i can`t find the problem on the internet. i`m using a hd intel ich9  adi1988B soundcard(soundsupreme fx2)..please help..thank you
(sorry for the spelling errors)

---

