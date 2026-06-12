---
title: "Matrioska"
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by Gouz on 2007-09-22
Greetings everyone.
Few minutes ago I tried to watch an anime on .mkv format and it couldnt I could normally watch all the other .mkvs but not this one. So I installed the Matrioska pack. Then the video that original was not playing was playing normally but all the rest weren't. After I unistalled the Matrioska pack nothing is playing not mkv's nor avi or anything else. And be playing I mean that the file is opened normally and then it crashes. I tried Totem Mplayer VLC and it is always the same.
I tried re installing the gstream and after it xine and libdvdcss2 but nothing helped.

Do you have any idea what  happened.

Thanks

---

### Post by RomeReactor on 2007-09-22
Hi. If you're using totem-gstreamer, try changing it to totem-xine and install the related codecs. If you don't have the Medibuntu repositories, [look here]("http://ubuntuforums.org/showpost.php?p=3399733&postcount=8") for instructions on how to add them and install the packages. If you **do** have the Medibuntu repositories, then just do:
```
sudo apt-get update
```
and just install the packages (the third instruction on the page I linked). Note that some matroska videos--particularly those using the h264 codec-- make totem choke, so use Mplayer to play them instead.

By the way, what do you mean by "I installed the Matrioska pack"? which pack would that be (a gstreamer package)?

---

### Post by Gouz on 2007-09-22
That is what I did:

deb [http://www.bunkus.org/ubuntu/feisty/](http://www.bunkus.org/ubuntu/feisty/) ./
deb-src [http://www.bunkus.org/ubuntu/feisty/](http://www.bunkus.org/ubuntu/feisty/) ./

apt-get update

apt-get install mkvtoolnix-mb.

I found it here
[http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu](http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu)

And then is when the real mess came in.

I have all ready than what you posted as an aswer
I tried totem-xine and the codecs and the updates but nothing came up nothing.

also when I run apt-get update I get this:
 Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_feisty_non-free_binary-amd64_Packages)

and then it says that if I want to fix it I have to run apt-get update but it is still there

---

### Post by RomeReactor on 2007-09-22
You probably added the medibuntu repositories again; please post the output of this:
```
cat /etc/apt/sources.list
```

---

### Post by Gouz on 2007-09-22
I found it...
The solution is this

First DON'T install the the matrioska that i did.. well maybe for you will work and I hope that it works but if the the things mess up that is that you have to do.

first install the matrioska and manualy delete from your source.list the things that you add and maybe have been added but the last update after the matrioska installazation.

Second remove all of your codecs and restart your computer that install all the codec you hade maybe it will still not be able to work but have faith in couple of beers and don't hit the keyboard ;)

Then use the 
code
echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

for more use this [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

Then a nice restart and you hope that it will work.

installing xine over gstream well it didn't work for me, maybe works for you and it is faster way to  fix everything.

And some info that I found about Totem chocking from the .mkvs yes it those that :( unfortunatly everything that is bigger than 200 (I didnt tried with 199.9 but I guess it is the same) killes totem and also big resolutions are making it die in your hands so yes as RomeReactor says use Mplayer give it a try (I hadnt done it until now) play with the options and you may like it ;) 

What I miss from windows is CCCP and Media player classic but I am still using linux :P

Have fun


Edit: Well it is a nice command that I didnt knew and yes I had done that and other stupid things were in my source.list but they are not anymore... I killed them all :P
Thanks for the help and for the new command ;)

---

### Post by shirilover on 2007-09-23
If you wish to watch anime with stylized subtitles, you should probably use a recent version of MPlayer which can render most styled subtitles.

The version in the multiverse repositiry should be fine.

---

### Post by Gouz on 2007-09-23
Everything is working now.
And the Mplayer is good I thing I will start using it again.
But now the sound died on me.. and I see that they are other people with the same problem :(
And i don't thing I can fix it :(

---

### Post by RomeReactor on 2007-09-23
Was sound working on Mplayer and then stopped? do you have an integrated audio card, or a SoundBlaster or other brand installed?

---

### Post by Gouz on 2007-09-23
rosi@rosi:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I think this is the card.

Now when I posted my last replay everything was working then I installed Mplayer and after about 5 min and a restart no sound from anywhere I got this message from Mplayer as well : Could not open/intialize audio device -> no sound. 

For videos the image was moving and same for the songs but no sound.
I found something in the forums which lead me to a crash of the gdm and then a format.
Now I still have the same problem no sound and now when I run a video or a song I can see the time the window stays open but nothing else is happening no sound and the file doesnt moves on the next second it is static.

Any ideas?
thanks

---

### Post by Gouz on 2007-09-24
Ok I fixed it.

The error was at the alsamixer

First I check my alsa version and I updated but somehow the old version was conflicing with the new.

Then it is when I turned of my internal microphone and I fixed the alsa but no sound.
now I turned on the mic and everything works.

Stupid me...

Thanks for your help ;)

---

