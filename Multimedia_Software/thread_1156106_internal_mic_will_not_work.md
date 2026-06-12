---
title: "internal mic will not work"
date: 2009-05-11
forum: Multimedia Software
---

### Post by shadowfoxx on 2009-05-11
I'm new to linux so please be kind...

I just blew away vista and installed ubuntu 9.04 on my lenovo y410 laptop. woot... everything seems good but for some reason I can't get the internal mic to work. If I plug in an external mic then that will work.. but I can't for the life of me figure out how to get the internal mic to work. 

I have tried going into the volume control and setting the input source to int mic but still nothing. Any help would be most appreciated. 

Thanks for your help.

---

### Post by shadowfoxx on 2009-05-11
Also... sound is working fine... webcam is working fine... and I tried changing the alsa-base.conf file to include  

model=lenovo-3000 <- didnt work
model=lenovo   <- didnt work

any suggesting would be great.

---

### Post by shadowfoxx on 2009-05-12
bump

---

### Post by leandromartinez98 on 2009-05-12
I had many problems like these in many machines. Usually the solution is some combinations of Sound Mixer settings and input sources, which I can hardly reproduce. I would try what you are trying, be sure that none of the volume controls is muted. Start by showing every option in the volume mixer.

---

### Post by shadowfoxx on 2009-05-12
thanks for the help. I added a screenshot of my alsamixer setting to my top post.

---

### Post by shadowfoxx on 2009-05-12
just an update.....I just upgraded to alsa .20... still no mic

---

### Post by shadowfoxx on 2009-05-13
anyone?

---

### Post by Digitallysick on 2009-06-29
I have the same model notebook, same problem

---

### Post by shadowfoxx on 2009-07-01
bump.. anyone know a solution to this?

I know that there is a launchpad ticket open for alc262 posted at the link below but that has been open for almost a year now with no resolution. Somebody has to have found a fix to this by now.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/141445](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/141445)

Anyone with any insight to this please help.

---

### Post by Digitallysick on 2009-07-14
My mic doesn't work either, its a real shame because i can't use skype

---

### Post by igorzwx on 2009-07-14
I use Skype with OSS4 it works fine.
no delay, no latency, no noise.
On any box.
Now I can call to Ukraine, Australia, and Chile, and everywhere.
Long live OSS!

---

### Post by Digitallysick on 2009-07-16
how did you get the mic to work with alc262, care to explain?

---

### Post by shadowfoxx on 2009-07-22
I just wanted to add that I have just found a way to get the internal mic to work. It's not really a fix as much as a workaround but either way it did the trick for me. Like I mentioned previously this is on my Lenovo y410 laptop which uses the alc262 drivers and using ubuntu 9.04 32bit. 

To get the mic to work I had to edit my alsa-base.conf file to trick it into thinking that it's an HP model that also uses alc262 instead of a lenovo. Everyone experiencing the problem of all audio working except for the internal mic can try the following which worked for me.

1) open up terminal and type: sudo gedit /etc/modprobe.d/alsa-base.conf 
2) add the following line to the end of the config file: options snd-hda-intel model=hp-bpc
3) save and close the config file
4) stop and restart pulseaudio by typing the following into terminal: 
   $ killall pulseaudio
   $ sudo alsa force-reload
   $ pulseaudio -D
5) now go into alsamixer by typing alsamixer in termial and edit it accordinly (changing the mic sourse from mic to front mic, etc...)

Your Done! :) test it.. it should be working now.

---

### Post by igorzwx on 2009-07-22
Hi [Digitallysick]("http://ubuntuforums.org/member.php?u=16573")

perhaps, you want to stay with alsa. Right?

if you feel very experimental, you can try OSS4 too.

---

### Post by shadowfoxx on 2009-07-23
the workaround that I posted above will work but only until I reboot .. Once I reboot then it stops working.. the config file stays the same but I have to change it back to lenovo .. reload pulseaudio.. then change it back to hp for it to work again...does anybody know why or how to fix that.


**Edit--- nevermind.. I figured out how to get it to work**

---

### Post by HarshReality on 2009-08-06
VERY interested in this as its also the case on my Vaio...

---

### Post by shadowfoxx on 2009-08-07
> **HarshReality said:**
> VERY interested in this as its also the case on my Vaio...

HarshReality... I know you sent me a pm so I am updating this thread so that you and others can see what I did. I don't know your experience level with linux is so if you need further step by step instructions just let me know and I would be more then happy to help out as much as I can.. keeping in mind that I am kinda brand new to linux myself.

Also, be aware that this is NOT a fix to the problem but just a workaround that I was able to figure out.

What I did:

1) I found a list of other pc brand/models that use alc262:

  fujitsu	Fujitsu Laptop
  hp-bpc	HP xw4400/6400/8400/9400 laptops
  hp-bpc-d7000	HP BPC D7000
  hp-tc-t5735	HP Thin Client T5735
  hp-rp5700	HP RP5700
  benq		Benq ED8
  benq-t31	Benq T31
  hippo		Hippo (ATI) with jack detection, Sony UX-90s
  hippo_1	Hippo (Benq) with jack detection
  sony-assamd	Sony ASSAMD
  toshiba-s06	Toshiba S06
  toshiba-rx1	Toshiba RX1
  tyan		Tyan Thunder n6650W (S2915-E)
  ultra		Samsung Q1 Ultra Vista model
  lenovo-3000	Lenovo 3000 y410
  nec		NEC Versa S9100
  basic		fixed pin assignment w/o SPDIF
  auto		auto-config reading BIOS (default)

2) I then went one by one adding the option for that model in my /etc/modprobe.d/alsa-base.conf file then killing and restarting pulseaudio to see if it worked.
   (Example. I added the line- options snd-hda-intel model=hp-bpc -to the bottom of my alsa-base.conf file to test the hp-bpc config from the list above.. then saved the alsa-base.conf file... and killed/restared the service ..open terminal and typed 

$ killall pulseaudio
$ alsa force-reload
$ pulseaudio -D

then went into alsamixer and checked the levels of everything and tested to see if it worked. if not then I did it all over again with the next pc/model in the list.)

I found that for my lenovo 3000 y410 laptop the model=hp-bpc option seemed to work... Great! I know what will work now.. BUT.. The only problem was that when I restarted my computer it would always loose all audio..so to correct that problem I made 2 copies of my alsa-base.conf file one with the options snd-hda-intel model=hp-bpc and one with the  options snd-hda-intel model=hp-bpc. I then edited /etc/gdm/PostSession/Default file so that it would copy the file with the lenovo option over on logout (so that on boot it would know I have a lenovo and give me sound) and edited the file /etc/gdm/PreSession/Default so that it would copy the file with the hp-bpc option over on login and kill/reload the service (thus giving me sound and internal mic). 

so far so good. this seems to be working.. like I said not the best fix in the world but now at least the audio and mic works.. and hopefully alsa will fix their crappy drivers.

**for Harshreality.. I have read somewhere that sony users have simply added the sony-assamd option to their alsa-base.conf file and audio and internal mic magically worked on reboot and stayed working.. so you might just want to try that first**

---

### Post by HarshReality on 2009-08-08
Yea, tried multiple settings (sony-assamd first was on the list) and no luck on that interal mic. Since my lap install is clean Im thinking of going to OSS4 over ALSA since Ive heard a great deal more positive result on their end.

Update: That was a bust.. I know it sounds trivial but I think I'll just have to hold till this gets resolved. I dont mind not having the ability to run Win apps that are intensive and cant use wine but I want my system 100% functional

---

### Post by shadowfoxx on 2009-08-08
sorry to hear that it didn't work for your machine HarshReality. If it is of any comfort I just checked the launchpad ticket that is open for alc262 ([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/141445](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/141445)) and supposidly the next version of alsa should resolve this problem :)

---

### Post by HarshReality on 2009-08-09
Well thats a plus I suppose. Im going to roll back to Intrepid and see what happens but for Jaunty the toshiba-s06 is ineffective. If I knew how to get a hold of and compile upstream Id go ahead and get that and get it over with.

---

