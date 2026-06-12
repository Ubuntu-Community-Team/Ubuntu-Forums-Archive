---
title: "Microphone works only after switching to another input setting and back."
date: 2010-05-07
forum: Multimedia Software
---

### Post by helbent forleder on 2010-05-07
Hi!
I have had a strange problem since 9.10.
My microphone works, BUT only after I open the 'Sound Preferences' panel, and change the setting under the 'Connector' tab to another selection (any will do), then set it back to 'Microphone 1'.
Since this works, I wondered if there is a way to make this happen automatically at every login?
Any help would be appreciated!
Thanks!

PS: 00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

---

### Post by helbent forleder on 2010-05-11
*bump* - is there anybody out there?

---

### Post by dolphinsonar on 2010-05-12
Working on this too, let me know if you figure anything out.  I will Google around a bit.

---

### Post by lidex on 2010-05-13
> **helbent forleder said:**
> Hi!
I have had a strange problem since 9.10.
My microphone works, BUT only after I open the 'Sound Preferences' panel, and change the setting under the 'Connector' tab to another selection (any will do), then set it back to 'Microphone 1'.
Since this works, I wondered if there is a way to make this happen automatically at every login?
Any help would be appreciated!
Thanks!

PS: 00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

Try pulseaudio volume control;
```
sudo apt-get install pavucontrol
```

---

### Post by helbent forleder on 2010-05-13
Thanks Lidex.
But what should that do?

Dolphinsonar: I filed a bug: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/577178](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/577178)

Not anything much happening with that yet.

---

### Post by dolphinsonar on 2010-05-16
hellbent forleder

Looking back at your original post, I am not sure which computer you are using.  So, not sure my solution will work for you.  But -- I got my Dell Inspiron 1318 working using this fix:

[http://ubuntuforums.org/showthread.php?p=9307284](http://ubuntuforums.org/showthread.php?p=9307284)

There is a database of settings that you need to manually enter into an ALSA configuration file if you are having audio problems like the mic not working, you might check it for your model:

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Hope that helps!

---

### Post by breefru on 2010-05-19
Hello, 
same problem here,
same motherboard

00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

 I must switch input device to mic 2 for exemple, and switch back to mic 1 into sound input setting, and mic is comming back.

Mic can also trigger on if I mute/unmute, and adjust input level

 Important information, it happens with skype, I must do further investigation to see if it is only skype related or not

---

### Post by helbent forleder on 2010-06-12
Thanks everyone - I fianlly found some time to check all of your links, which led me to this... 

[http://ubuntuforums.org/showthread.php?t=820959]("http://ubuntuforums.org/showthread.php?t=820959")

Breefru, just open the terminal and do:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Add a new line at the end of the document with:

```
options snd-hda-intel model=6stack
```

Save it and reboot. :)

Thanks again everyone! I really appreciate your help!

---

