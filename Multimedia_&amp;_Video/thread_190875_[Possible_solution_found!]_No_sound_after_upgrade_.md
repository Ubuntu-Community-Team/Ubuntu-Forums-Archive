---
title: "[Possible solution found!] No sound after upgrade to Dapper from Breezy"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by techmonkey on 2006-06-06
So after upgrading to Dapper I had no sound. I trawled these forums and Google but only found other people in my situation.

I consulted the Ubuntu IRC channel, but my question got swamped by lots of others. It's a fast paced channel. 

So anyway, I ask out of frustration, my same quesiton to the lovely folks on the #lugradio channel on irc.freenode.org. Somebody there said I should use apt-get source alsa-base to download the source of ALSA and compile my own DEB file.

I now have sound! woot!

Type the following into a terminal window:

```

sudo /etc/init.d/alsa stop
[best to stop ALSA first, if it's running at all]

cd $HOME
mkdir alsasrc
cd alsasrc
apt-get source alsa-base
[note: sudo is not needed for a source code download]

cd alsa-driver-1.0.10
fakeroot debian/rules binary
[caveat: you may need to sudo apt-get install fakeroot first]

[let it create the deb for you, and then install it with dpkg:]

cd ..
[cd back to the main src directory we started in]
dpkg -i alsa-base_1.0.10-4ubuntu4_all.deb

```

Fingers crossed and good luck!
NB. I didn't get an init script with this method, so I'm not sure how to start ALSA.  I also didn't stop ALSA beforehand, so to stop the old ALSA running I restarted my system. In the process, Ubuntu started my newly installed ALSA.

And now sound works perfectly.
You'll want to not use ESD though - it hogs the sound card. System -> Preferences -> Sound -> untick the box which says 'Enable software sound mixing (ESD)'.

For the precise amongst us, typing killall -9 esd will force it to end now. Repeating that command and getting 'No process killed' will confirm it has stopped.

Best of luck!

---

### Post by Zhukov on 2006-06-06
I wonder if this will give me the 5.1 sound i want :P

---

### Post by jetpeach on 2006-06-06
interesting, i tried doing exactly as you said, after the "fakeroot debian/rules binary" command i got the error ```
debian/rules:16: /usr/share/dpatch/dpatch.make: No such file or directory
make: *** No rule to make target `/usr/share/dpatch/dpatch.make'.  Stop.
```  
Also, would you mind clarifying how this is better than getting alsa from the repos?  I believe I have been using also, but am supposing this is a newer version with significant improvement or?

Thanks!

---

### Post by crimsun on 2006-06-06
[QUOTE=techmonkey]So after upgrading to Dapper I had no sound. I trawled these forums and Google but only found other people in my situation.[/QUOTE]

Arguably it is worthwhile as well to file a bug in Malone against linux-source-2.6.15 if your sound broke on dist-upgrade from Breezy to Dapper. That is in fact the preferred catalyst for getting your issue resolved (at least for me, since I tend to triage the sound bugs for Ubuntu).

Relevant information that I'll need includes output from the following commands:

lspci -nv
lsmod
tail -2 /proc/asound/oss/sndstat
amixer

---

### Post by nathan_balon on 2006-06-07
I also had a problem with the no sound after I upgraded to drapper.  I checked my sound card and everything looked ok.  I also chekced the master volume and PCM and those were set so I would receive sound.  It took me a few minutes of playing around till I found the problem.

I fixed the problem by opening alsamixer.  I scrolled down to the end of the mixer and by raising the levels the sound worked again.  I had four levels I could adjust label VIA DXS.  I think they may be labeled different depending on the sound card the computers uses.  You may want to try to adjust those settings and see if it fixes your problem before compiling alsa.

---

### Post by techmonkey on 2006-06-27
[quote=jetpeach]interesting, i tried doing exactly as you said, after the "fakeroot debian/rules binary" command i got the error 
```
debian/rules:16: /usr/share/dpatch/dpatch.make: No such file or directory
make: *** No rule to make target `/usr/share/dpatch/dpatch.make'. Stop.
```
 
Also, would you mind clarifying how this is better than getting alsa from the repos? I believe I have been using also, but am supposing this is a newer version with significant improvement or?[/quote]
 
Ah. You'll also need to ```
sudo apt-get install dpatch
```. Sorry about that. After installing that you ought to have everything you need to compile your own deb.
 
This was really a last resort for me as I guessed, guided by people on IRC that the default bundled ALSA package is unhappy and compiling your own deb by the method shown above would work magically somehow. It did work at first, but I still have to work out how to get multiple applications to share the soundcard.
 
Please don't tell me we still haven't got *that* little feature sorted out of the box yet! Two certian rival operating systems have had this for yonks!
 
[quote=Crimsun]Arguably it is worthwhile as well to file a bug in Malone against linux-source-2.6.15 if your sound broke on dist-upgrade from Breezy to Dapper. That is in fact the preferred catalyst for getting your issue resolved (at least for me, since I tend to triage the sound bugs for Ubuntu).
 
Relevant information that I'll need includes output from the following commands:
 
lspci -nv
lsmod
tail -2 /proc/asound/oss/sndstat
amixer[/quote]
 
I'm not at my home machine (or even an Ubuntu machine) at the moment, so I'll send myself an e-mail reminder and do it when I get home.
 
Sorry about the delay in posting here, I'm more of a mailing list person these days.

---

### Post by nick holme on 2006-06-27
I had a problem with recording - there was no input on mic or line. I tried audacity and also the small sound recorder utility. After reading Nathans post (see earlier) I installed the alsa mixer gui and found that the volume was turned to minimum on both these channels. Once I turned these up, I was OK. Thanks Nathan.

---

