---
title: "Can't get audio on 9.04 with VIA 8235 soundcard"
date: 2009-06-26
forum: Multimedia Software
---

### Post by stupac on 2009-06-26
I followed the comprehensive sound problem solutions guide already. 

**Here's what I did before that which screwed things up more:**
After installing it appeared to have detected my soundcard successfully, but I got no sound from speaker-test or anything. I made sure all the switches and settings in the volume control were set right, then I went a screwed things up worse by installing some VIA ALSA patch I found on VIA's website, ultimately I ended up with null output. I uninstalled the VIA software, but still couldn't get it back to how it was when I had first installed.

**Here's where I am now:**
 After that I found the stickied thread and followed the solutions guide through to ALSA driver compilation. I didn't get any errors after compiling with the alsa-source and the module-assistant so I followed it back to step 4 and here's where I am stuck.

```
$ sudo modprobe snd-via82xx
WARNING: Error inserting gameport (/lib/modules/2.6.28-13-generic/kernel/drivers/input/gameport/gameport.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_via82xx (/lib/modules/2.6.28-13-generic/updates/alsa/pci/snd-via82xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```and 
```
$ dmesg | tail
[  764.232190] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[  764.232193] snd_ac97_codec: Unknown symbol ac97_bus_type
[ 2075.341617] snd_ac97_codec: Unknown symbol snd_hidden_kzalloc
[ 2075.342235] snd_ac97_codec: Unknown symbol snd_hidden_kcalloc
[ 2075.342474] snd_ac97_codec: Unknown symbol snd_hidden_kfree
[ 2075.342716] snd_ac97_codec: Unknown symbol snd_verbose_printk
[ 2075.343341] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[ 2075.343344] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[ 2075.343731] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[ 2075.343734] snd_ac97_codec: Unknown symbol ac97_bus_type 

```I'm afraid I have no idea how to proceed from here. I'd appreciate some help. I've been using Ubuntu on numerous machines for years, this is the first one I've ever had sound problems beyond just a switch in the mixer. Thanks!

---

### Post by tolotos on 2009-06-27
Are you sure, you removed all the old alsa modules and files before compiling alsa? Since he is disagreeing about some versions, I suppose, that some alsa modules were still loaded in the kernel when you compiled alsa and therefore couldn`t be replaced with the new ones.

---

### Post by stupac on 2009-06-27
Thanks for the reply, tolotos. I don't know, I never attempted to remove any alsa modules. I don't really know what I'm doing I'm afraid. Anyways, how do I proceed? I assume I need to make sure the old modules are removed and then recompile and install the new alsa modules? How do I remove the old ones?

---

### Post by tolotos on 2009-06-27
The problem of having the old modules not removed, is caused by them being used by programms. I asume you did all the compiling inside a terminal in a gnome session. Alongside with gnome many programms are running, and some might use the a kernel mordule related to alsa (If you want to check wich modules are currently loded try "lsmod" in console). If there was an alsa module (that are the ones containing "snd") loded, as you compiled the new modules, it couldn`t be replace because it was write-protected (due to it being loaded). Now you have different versions of modules installed. The one that weren`t loaded are newer than the ones that were loaded. Thats the reason for you getting vserions disagreement. 
I would suggest you should restart and boot in rescue mode to a root schell. This has the benefit, that gnome and all the other apps aren`t startet. In this terminal try:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
```[SIZE=2]
[/SIZE]This will remove all alsa related stuff and reinstall it from the repositorys. After that reboot your PC.
But be carefull!!! As described in the sound solutions guid be prepaired to do a
```
sudo apt-get install gdm ubuntu-desktop
```again, if your gnome gets uninstalled too.
You won`t be using the newest versions in comparison to compiling it from source. But at least 
```
sudo modprobe snd-via82xx

```should work again. If this works wo could further trace down the problem, because I personally don`t believe that it results from the alsa modules.
Just write again, after following the steps above and we shall see what can be done.

---

### Post by stupac on 2009-06-27
Thanks for the help tolotos, that got me back to the post-ubuntu-installation state. I now have the module installed and I can see the device in the mixer again, checked all the switches and levels, but can't get audio to output as before. I appreciate all the helps so far, where do I go from here? I don't know where to begin diagnosing this issue.

---

### Post by tolotos on 2009-06-28
Ok now I would try the following:
1) Open a music file in your favourite music-player (for example audacious).
2) Go to preferences -> output options (ore anything similar).
3) Select as output source "alsa" instead of "pulseaudio".
4) Eventually restart your audio player and check whether you hear any sound.
If there is sound, you know that alsa is working fine and that pulsaudio is the problem.
If there is still nothing to hear, it would be useful if you could attach screenshots with your alsamixer configuration.

---

### Post by stupac on 2009-06-28
Success! That did it, thanks tolotos. Don't know how I can thank you enough! I owe ya a six pack or something if you are ever in town.

---

