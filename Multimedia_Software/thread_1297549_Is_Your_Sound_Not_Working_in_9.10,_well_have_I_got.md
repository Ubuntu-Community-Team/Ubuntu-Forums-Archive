---
title: "Is Your Sound Not Working in 9.10, well have I got the solution for you!"
date: 2009-10-21
forum: Multimedia Software
---

### Post by jmate24 on 2009-10-21
First of all after searching the forums for my sound card and why it did not show up after my laptop went into suspend, sleep or hibernate. I stumbled on to this thread:

[HTML]http://ubuntuforums.org/showthread.php?t=1296221[/HTML]

Where I was subsequently lead to the Ubuntu Help webpage on Sound Troubleshooting:

[HTML]https://help.ubuntu.com/community/SoundTroubleshooting[/HTML]

then it lead me to git.alsa-project.org the specific web page is here:

[HTML]http://git.alsa-project.org/?p=alsa-kmirror.git[/HTML]

where I noticed that they are going to remove the suspending of the sound card by the system when ever your pc/laptop enters sleep, suspend or hibernate.

So then I remembered back to when I was having problems with my sound card for 9.04 and then it hit me about the alsa-base.conf file and how it has the lines about the sound card being configured to suspend whenever my laptop enters sleep, suspend or hibernate and so I entered this command into the terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

I commented out these configuration lines in the file:

```
# Power down HDA controllers after 10 idle seconds
# options snd-hda-intel power_save=10 power_save_controller=N
```

Next I went back to this web page and found out how to not only reload my sound card but make it so that every time I boot, reboot or wake my computer from its sleep modes that the sound driver is always loaded:

[HTML]http://ubuntuforums.org/showthread.php?t=1296221[/HTML]

First I entered this into the command line (or terminal) to reload my driver.

```
sudo alsa force-reload
```

Second I entered this command to find my driver which is found by using this command:

```
lspci -v
```
 
Then I added my driver to a new line at the bottom of the /etc/modules file you access it with the terminal using this command:

```
gksudo gedit /etc/modules
```

Finally I rebooted (WHICH IS A MUST) in order to get my sound to work properly.

Now I can Listen to Rhythm Box, VLC, Games and Streaming web content with ease.

jmate24--

---

### Post by matches on 2009-10-21
> Then I added my driver to a new line at the bottom of the /etc/modules file you access it with the terminal using this command:

How is this supposed to look? I see my sound card with all sorts of data. Do I include it all or just the driver name?

Thanks

---

### Post by jmate24 on 2009-12-22
just the name.

snd-hda-intel is my driver name.

snd-viaxxxx is another type of driver name where xxxx is the chipset number? i think.

jmate24--:)

---

