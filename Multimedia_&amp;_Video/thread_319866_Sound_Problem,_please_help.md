---
title: "Sound Problem, please help"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by Dekunuts on 2006-12-16
Okay, so I posted a thread on this problem weeks ago but no one could solve it. I'm trying once more, in the hope that someone can help me. I will quickly an clearly describe what the situation is (not why I changed the cards etc, that's not important).

- Installed Breezy and used on board sound (Nforce2 on K7N8X-X), worked great
- Upgraded system as time went on
- Installed Hercules Gamesurround sound card, worked great and i didn't do anything
- Upgraded to Edgy, worked great
- removed Hercules card, wanting to use onboard again
- no sound

I haven't had sound for over a month and I don't know what to do. aplay -l is capable of identifying the soud card and no software knows that there is a problem (Rhytmbox etc all play and work as if the sound works, but there's nothing). I also tried reinstalling the alsa-utils and those other sound related packages, but it didn't help (except for having to do a sudo apt-get install gdm ubuntu-dektop ](*,) )Maybe it's as simple as an alsamixer setting, but I don't know what all those things mean, so here is a screenshot. 

[http://home.versateladsl.be/mcourtea/alsa2.png](http://home.versateladsl.be/mcourtea/alsa2.png)

Please help.

Also, I do know reinstalling will fix this but I'm not doing that because of all my data etc. and also because that is not the way i like to fix problems.

---

### Post by Dekunuts on 2006-12-17
why can't anyone help me, not one hint or small tip or a bit of hope, just nothing. I give up

---

### Post by deadgobby on 2006-12-17
You say you removed your sound card right? You may want to check your BIOS and see if the on board sound is set correctly. Either off or on. 
Gobby

---

### Post by total wormage on 2006-12-17
this looks a bit like you've been editing your /etc/modprobe.d/alsa-base file and your ubuntu still uses the hercules sound card as default :]

why don't you _completely_ remove the alsa-base package and reinstall it?

---

### Post by Dekunuts on 2006-12-17
Ah great, answers. 

The bios settings are correct, although a bit annoying, the only options I have are -disabled- and -auto- 

Well, i removed the alsa-base linux -sound-base and alsa-utils like five times already. The first time that didn't work, so then I did it again with the --purge so that everything about it, including config, would be removed (that's what i think --purge does anyway). But it didn't help either. I have already done that like 5 times and it's not working. I also tried reinstalling the whole sound thing using three different kernels, but that didn't work either. 

Now after weeks of trying, today i put a different pci card in this morning but the computer doesn't even list it when i do aplay -l, it doesn't even list it under pci devices. That sucks but because it's apparently invisible, i left it there and turned my onboard sound on again in the hope of getting it to work.

I also thought i might have been gstreamer problem but xine doesn't work either. I really don't know what the problem is. The most annoying thing is that i don't get any errors at all from anywhere. It just doesn't work.

---

### Post by total wormage on 2006-12-17
i only install things with apt, don't remove or purge them, so i don't really know what purge does

if you have synaptic installed, try completely remove alsa-base there
and excuses if you've also done that already multiple times ;]]]

otherwise, good luck!

---

### Post by Dekunuts on 2006-12-17
so i tried a complete removal of alsa-base alsa-utils and linux-sound-base through synaptec, didn't change anything. What really bothers me is that when i completely remove a package and then reinstall it (with reboot inbetween) it doesn't have to download at all. It gets it from somewhere on the harddrive. I have a feeling this could be a problem.

---

### Post by total wormage on 2006-12-17
odd.

does /etc/modprobe.d/alsa-base still exist after removal? :]

btw i respect your drive to solve this problem other then just reinstall ubuntu (which i would have done a LONG time ago when encountering this problem :p)

and did you 'sudo apt-get update' before reinstalling the package? :]

---

### Post by Dekunuts on 2006-12-17
I'm going to try what you said right away, I have not done apt-get update, going to try that to, I will let you know how it turns out

---

### Post by Dekunuts on 2006-12-17
so, I deletd the packages again with synaptec (complete removal). Then rebooted into command line (because gdm and ubuntu-dektop get deleted as well) then checked if the alsa-base file was still there, it wasn't. Then i did the apt-get update and reainstalled the packages. Once again it did not download from the internet but installed from HDD. Then i ran alsamixer (still from command line) and everything was muted. I left it muted and then rebooted into gnome.

Now when i started alsamixer in gnome, nothing was muted, settings had changed between the reboot. Weird. Anyways it's not working and I am once again where i started 

I took another screenshot that may provide information for helping me. 

[http://home.versateladsl.be/mcourtea/Screenshot-1.png](http://home.versateladsl.be/mcourtea/Screenshot-1.png)

---

### Post by Dekunuts on 2006-12-18
please, someone prove me that the community works

---

