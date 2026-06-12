---
title: "amarok 2 not working in jaunty"
date: 2009-04-26
forum: Multimedia Software
---

### Post by nims_420 on 2009-04-26
hi,
I recently installed ubuntu 9.04 (gnome). I installed amarok 2 in it, but t is not playing ne files, it says "Too many errors in playlist". If any one knows how to fix this, plz let me know. Also, can some1 tell me how to play .wma files in exaile??

thanx

---

### Post by cherva on 2009-04-26
I have the same problem I installed phonon-backend-exine and now amarok 2 opens the mp3 file and I can see it is playing, but no sound is comming out ... By the way I upgraded one of my virtual machines to kubuntu 9.04 and the same problem occurs there..... 
I'm using OSS v4

---

### Post by dhavalbbhatt on 2009-04-26
Same here!

---

### Post by scythe01 on 2009-04-26
I am experiencing the same. I hope someone can tell us why it is happenng and how we can resolve it

---

### Post by dave r on 2009-04-26
Same here upgraded to 9.04 got the new Amarok with the upgrade and no sound in Amorak. Rhythm box working and everything else. Tried a number of fixes from here but still no sound in Amarok.

---

### Post by fontis on 2009-04-26
I also have the same problem.
I installed 9.04 yesterday and spent numerous hours trying to get Amarok to work. It gives some error message like "HDA intel<thensomethinghereididntpayattentiontoo> not working".

Banshee works though :)

---

### Post by cherva on 2009-04-26
Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/349847]("https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/349847")
Try to install phonon-backend-xine
```
sudo apt-get install phonon-backend-xine
```
And if you are in luck this will fix it. However it didn't helped me.
With OSS v4.

---

### Post by ubigT on 2009-04-26
sudo apt-get install phonon-backend-xine

This worked for me!
Amarok 2 in 9.04, it wouldn't make a sound before now.

---

### Post by Claritux on 2009-04-26
phonon-backend-xine solved the problem for me. Thanks!

---

### Post by skotos on 2009-04-26
> **ubigT said:**
> sudo apt-get install phonon-backend-xine

This worked for me!
Amarok 2 in 9.04, it wouldn't make a sound before now.
It worked for me, too! Thanks a lot, guys!

---

### Post by HammerHed on 2009-04-26
sudo apt-get install phonon-backend-xine - Fixed the problem for me too.

---

### Post by cherva on 2009-04-26
[COLOR="Red"]**OSS HOWTO:**[/COLOR]
1) Download this file: [http://www.fileupyours.com/view/77985/libphonon.conf]("http://www.fileupyours.com/view/77985/libphonon.conf")
2) Put it in:~/.config/kde.org/ (where ~/ means your home directory) You may need to create the kde.org directory
3) If you don't have phonon-backend-xine install it.
```
sudo apt-get install phonon-backend-xine
```
4) Restart Amarok 2 and have fun.

---

### Post by markbuntu on 2009-04-26
Well all that did not work for me. What I eventually did after doing all that was suggested in the earlier posts was get the xine-gui and change the setting in audio to pulseaudio. Now amarok shows up in the pulseaudio volume control like it should. This is with the gnome desktop.

If you are using KDE/Kubuntu you can play with the system settings/multimedia.

---

### Post by donkeyX on 2009-04-30
I am having the same problem but none of these have found me a solution :(. I would like to try the gui that you mentioned markbuntu xine-gui, but cannot find it in the repos.

---

### Post by rberidon on 2009-04-30
> **markbuntu said:**
> Well all that did not work for me. What I eventually did after doing all that was suggested in the earlier posts was get the xine-gui and change the setting in audio to pulseaudio. Now amarok shows up in the pulseaudio volume control like it should. This is with the gnome desktop.

An adaptation of this worked for me.  I installed xine-ui and changed the audio engine in audio (you must change GUI->Configuration Expert level to higher than Beginner) and then audio -> Audio Driver to alsa.  I'm not sure of the differences between pulseaudio and alsa but alsa is what I tried first because that's what is selected in the system Volume Manager.

Reinstalling photon-backend-xine did nothing for me.

---

### Post by markbuntu on 2009-04-30
> **donkeyX said:**
> I am having the same problem but none of these have found me a solution :(. I would like to try the gui that you mentioned markbuntu xine-gui, but cannot find it in the repos.

Ooops, sorry that was a typo. it is 

xine-ui.

---

### Post by markbuntu on 2009-04-30
> **rberidon said:**
> An adaptation of this worked for me.  I installed xine-ui and changed the audio engine in audio (you must change GUI->Configuration Expert level to higher than Beginner) and then audio -> Audio Driver to alsa.  I'm not sure of the differences between pulseaudio and alsa but alsa is what I tried first because that's what is selected in the system Volume Manager.

Reinstalling photon-backend-xine did nothing for me.

Are you using 64 bit Jaunty?
That's what I am using. The missing phonon-backend-xine seems to be a 32 bit problem since amarok pulled it in as a dependency for me on 64 bit and the xine-ui seems to be the only way to change the xine default driver.

---

### Post by amporio on 2009-04-30
> **markbuntu said:**
> Are you using 64 bit Jaunty?
That's what I am using. The missing phonon-backend-xine seems to be a 32 bit problem since amarok pulled it in as a dependency for me on 64 bit and the xine-ui seems to be the only way to change the xine default driver.

buenas mi spanish,  mi solucion

Instalando Amarok 1.4 en Ubuntu Jaunty

Lo primero es agregar un par de repos a tu sources.list.

deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main

Luego debes importar la llave del repositorio para que apt no te lo reclame.

sudo apt-key adv --recv-keys --keyserver \
keyserver.ubuntu.com 0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63

Luego hace un update y luego instalar:

$ sudo apt-get update
$ sudo apt-get install amarok14

Nota: El paquete de amarok 1.4 se ha renombrado a amarok14 para evitar conflictos son amarok 2.

---

### Post by pajdina on 2009-05-04
> **donkeyX said:**
> I am having the same problem but none of these have found me a solution :(. I would like to try the gui that you mentioned markbuntu xine-gui, but cannot find it in the repos.

sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%

---

### Post by theglowblue on 2009-05-04
same issue

same solution

sudo apt-get install phonon-backend-xine

thanks much

---

### Post by svivian on 2009-05-05
> **rberidon said:**
> An adaptation of this worked for me.  I installed xine-ui and changed the audio engine in audio (you must change GUI->Configuration Expert level to higher than Beginner) and then audio -> Audio Driver to alsa.  I'm not sure of the differences between pulseaudio and alsa but alsa is what I tried first because that's what is selected in the system Volume Manager.

This worked for me, thanks!

---

### Post by gooz89 on 2009-05-05
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%


This worked for me, thanks pajdina

I have Jaunty 64 for anyone else with this problem.

---

### Post by Jesper Ø. Jensen on 2009-05-06
Ubuntu 9.04 and Amarok 2.0

This worked for me too: 

sudo apt-get install phonon-backend-xine

---

### Post by Pitboss on 2009-05-06
> **rberidon said:**
> An adaptation of this worked for me.  I installed xine-ui and changed the audio engine in audio (you must change GUI->Configuration Expert level to higher than Beginner) and then audio -> Audio Driver to alsa.  I'm not sure of the differences between pulseaudio and alsa but alsa is what I tried first because that's what is selected in the system Volume Manager.

Reinstalling photon-backend-xine did nothing for me.

Where exactly can I find "GUI->Configuration Expert", cause there are not much options that I can tweak in amarok now, and I really don't like messing with System > Preferences > Sound settings?

---

### Post by Nidding on 2009-05-06
> **rberidon said:**
> An adaptation of this worked for me.  I installed xine-ui and changed the audio engine in audio (you must change GUI->Configuration Expert level to higher than Beginner) and then audio -> Audio Driver to alsa.  I'm not sure of the differences between pulseaudio and alsa but alsa is what I tried first because that's what is selected in the system Volume Manager.

Reinstalling photon-backend-xine did nothing for me.
This worked for me as well. Thanks a lot, I was about to go crazy over this :D

---

### Post by Nidding on 2009-05-06
> **Pitboss said:**
> Where exactly can I find "GUI->Configuration Expert", cause there are not much options that I can tweak in amarok now, and I really don't like messing with System > Preferences > Sound settings?

You have to open the xine-ui (you might need to install it from synaptec), there you can go to settings and there's a tap called GUI.

---

### Post by Pitboss on 2009-05-06
> **Nidding said:**
> You have to open the xine-ui (you might need to install it from synaptec), there you can go to settings and there's a tap called GUI.

Thanks, now I got it. Now I have sound in amarok, but when it's playing I don't have any other sound like the flash player and rythmbox are muted. Anyone with the same problem?

---

### Post by vietunion on 2009-05-06
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%

Great, work for me, thank very much :)

---

### Post by Bishop Hill on 2009-05-07
Almost the same problem, same solution, thanks!

---

### Post by castudil on 2009-05-07
Got a 64 bit version of ubuntu and upgrade to jaunty... as other users pointed my amarok 2 looked great but didnt play music :S

Followed the steps mentioned and now amarok plays music, at least I have tested mp3 files.

BUT

Submission to last.fm are not working.  any solutions to this?

I filled in the info of my last.fm account then choosed TEST and the dialog box seems to be frozen, after a while I just close the window.. tried this a comple of times with the same result. Dont know if this can give a clue of why integration with last.fm doesn't work.

---

### Post by siylence on 2009-05-07
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%

This worked for me! Thanks!

---

### Post by flyboy917 on 2009-05-09
> **rberidon said:**
> An adaptation of this worked for me.  I installed xine-ui and changed the audio engine in audio (you must change GUI->Configuration Expert level to higher than Beginner) and then audio -> Audio Driver to alsa.  I'm not sure of the differences between pulseaudio and alsa but alsa is what I tried first because that's what is selected in the system Volume Manager.

Reinstalling photon-backend-xine did nothing for me.

This worked for me too but you also have to make sure you going into the system volume control and change the playback sound control to pure ALSA...no device association.

:KS

---

### Post by drkitty on 2009-05-16
If adding phonon-backend-xine doesn't work for you, make sure you don't also have the phonon-backend-gstreamer package installed. If so, just remove it. Worked for me. I found this tip here: [http://mcguyverofbeer.com/?p=284](http://mcguyverofbeer.com/?p=284)   ;)

---

### Post by Matt 6:27 on 2009-05-17
"sudo apt-get install phonon-backend-xine"  did the trick for me as well...

...life is good.

---

### Post by adambh on 2009-05-18
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%



Thanks pajdina, all is working now! sudo apt-get install phonon-backend-xine didn't work by itself.

---

### Post by KWhistle on 2009-05-18
phonon-backend-xine worked to play sound.  Still having trouble figuring out how to set up my song collection stored on the win partition.  Amarok just doesn't see it.  I posted about it on another thread, but seems that nobody has a solution as of yet.

K

---

### Post by glaze on 2009-05-18
If I have Amarok 2 open, I cannot hear anything else, like sound from Flash or MPlayer unless I close Amarok. I didn't have this problem on Kubuntu 8.10 and Amarok 1.4. My sound chip is Intel HDA.

edit: I installed Amarok 1.4 from PPA and now everything works ok again. Hopefully Amarok2 works in Kubuntu 9.10 Karmic.

---

### Post by umj on 2009-05-19
sudo apt-get install phonon-backend-xine libxine1-ffmpeg


100% working Tanks:guitar::lolflag:

---

### Post by miceagol on 2009-05-19
I had to [follow this guide]("http://tygertown.us/blog/2009/05/amarok-in-gnome-on-jaunty/") to get it working, since Amarok probably used my analog output as default when it was supposed to use the digital output.

---

### Post by khaos28 on 2009-05-19
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%


This worked for me, while nothing else did, THANKS!!

Jake

---

### Post by Pitboss on 2009-05-20
Hey, does anyone experience this - When vlc and amarok or skype and amarok are on the can't both have sound? I don't know why this is happening but really don't like it.

---

### Post by sauvik on 2009-05-22
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%

thanks a lot man.. worked for me.

---

### Post by benign on 2009-05-23
Thanks pajdina! I was looking for this for.. a whole minute! haha. I'm spending longer writing this than I did to get amarok working, thanks to you.

---

### Post by darkghost2 on 2009-05-23
thanks everybody for help ,i have missed AMAROK

---

### Post by bismark on 2009-07-15
> **miceagol said:**
> I had to [follow this guide]("http://tygertown.us/blog/2009/05/amarok-in-gnome-on-jaunty/") to get it working, since Amarok probably used my analog output as default when it was supposed to use the digital output.

This worked perfectly for me, I could either use Amarok2 or play videos in Firefox but not both.  I followed the guide and made pulseaudio the first selection for the preferred output method.

---

### Post by jetta on 2009-07-16
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%

works with me too, thx:D

---

### Post by _rH on 2009-07-23
> **markbuntu said:**
> Well all that did not work for me. What I eventually did after doing all that was suggested in the earlier posts was get the xine-gui and change the setting in audio to pulseaudio. Now amarok shows up in the pulseaudio volume control like it should. This is with the gnome desktop.

If you are using KDE/Kubuntu you can play with the system settings/multimedia.

Thanks :D, worked for me,  ubuntu 9.04, amarok 2.0.2.
I'd similarly had issues with amarok not playing mp3's nor net radio streams / podcasts
: close amarok --> xine-ui --> expert mode --> pulseaudio --> open amarok --> works!

---

### Post by rubaiyati on 2009-07-26
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%




Thanks, it works :P

---

### Post by rksingh54 on 2009-08-08
> **skotos said:**
> It worked for me, too! Thanks a lot, guys!

Those for who the Amarok working after installing with:
sudo apt-get install phonon-backend-xine

Are you using Jaunty 64 bit or 32 bit?

I have tried everything on my 64 bit machines, unsuccessfully. Rythmbox music player works fine.

---

### Post by rksingh54 on 2009-08-08
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%

Thanks a million. 

sudo apt-get install phonon-backend-xine libxine1-ffmpeg

It is did the trick, singing like a canary now.

---

### Post by rakesh_roshan on 2009-08-19
[B]sudo apt-get install phonon-backend-xine libxine1-ffmpeg

[/B]This worked for me.

---

### Post by allanandr3w on 2009-08-20
installed libxine-ffmpeg, its now working! thanks..........

---

### Post by j2deezy on 2009-08-20
i have tried

sudo apt-get install phonon-backend-xine

and all that comes up is

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



what hte hell..this is getting real annoying..and when i click play it says its playing but the length isnt even going so it isnt even playing..no sound..ugh help please i am using the upgrade to 9.04 (jaunty)

---

### Post by Helaya on 2009-08-30
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%

Thanks, I also had the same problem and solved. Tks pajdina

---

### Post by vishnu_sresht on 2009-10-01
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%



Yup! I already had phonon-backend-xine installed, installing libzine1-ffmpeg worked for me.

-----
Ubuntu 9.04 64-bit

---

### Post by reyquito on 2009-11-02
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%

That worked for me too.

Chas gracias, Don.

---

### Post by cusinmex on 2009-12-17
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%



thxxxx:biggrin:

this worked for me

---

### Post by Logical Dream on 2010-02-21
> **pajdina said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

and restart amarok2 works 100%


This worked for me ! Thank You 


p.s. on my desktop I just needed to select PulseAudio sound server for Output device , but on lap top didnt help

---

