---
title: "Wireless disabled by hardware switch"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by grimey44 on 2011-08-16
I think I have a similar problem as a bunch of people on here. I have 11.04 and wifi was working great until I flipped the wifi switch and now it won't work. 
I have an hp pavilion dv2500 laptop. 
I've tried a few o the suggested fixes but nonlick as of yet. 
Any help would be great. 
Thanx!

---

### Post by dave01945 on 2011-08-16
whenever i have had this problem i usually fix it by running

```
rfkill unblock all
```

hope this helps

---

### Post by chili555 on 2011-08-16
> **grimey44 said:**
> I think I have a similar problem as a bunch of people on here. I have 11.04 and wifi was working great until I flipped the wifi switch and now it won't work. 
I have an hp pavilion dv2500 laptop. 
I've tried a few o the suggested fixes but nonlick as of yet. 
Any help would be great. 
Thanx!nonlick, eh?

Let's see:```
rfkill list all
```Thanks.

---

### Post by grimey44 on 2011-08-16
I'm doing this from my phone and don't have a way to copy and paste code from my computer yet but here's what I got:

1: phy0: Wireless LAN
              Soft blocked: no
              Hard blocked: yes

---

### Post by chili555 on 2011-08-17
Is the module *hp-wmi* loaded?```
lsmod | grep wmi
```If it is, remove it temporarily as an experiment:```
sudo rmmod -f hp-wmi
```Now does the switch respond as expected? I worked on a case a few weeks ago where the *hp-wmi* module did not correctly translate the Fn+F12 wireless switch combination to turn on the wireless. By experimentation, he learned that the working combination was Alt+F12. I suggest you try various combinations, not just Alt and not just F12 to see if it works.

If *hp-wmi* is not loaded, load it and see if the switch or key combination works as expected:```
sudo modprobe hp-wmi
```

---

### Post by grimey44 on 2011-08-17
```
lsmod | grep wmi
``` gets me this:

```
snd_rawmidi            25269  1 snd_seq_midi
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```


```
sudo rmmod -f hp-wmi
``` after entering this, still no wireless.

and loading hp-wmi seems to hav no effect as well.

when i tried removing or loading hp-wmi, once the code was entered it asked for password then didnt do anything once entered. is that normal or should there be some sort of output from entering those?

---

### Post by dave01945 on 2011-08-17
my laptop doesn't even have a hardware switch but sometimes it will get hard blocked this command always works

```
rfkill unblock all
```

sometimes i do have to run it several time before it will work

---

### Post by chili555 on 2011-08-17
> **grimey44 said:**
> 

when i tried removing or loading hp-wmi, once the code was entered it asked for password then didnt do anything once entered. is that normal or should there be some sort of output from entering those?That simply means that the command was executed as directed and that there are no errors or warnings to report. Ideally, that's what we expect. Please try again:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Any improvement?

Please try all the key combinations as I explained above.

---

### Post by grimey44 on 2011-08-18
still no luck.

```

1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```

---

### Post by grimey44 on 2011-08-19
bumpbump

---

### Post by s031jd on 2011-08-19
[LIST=1]
[*]sudo rfkill list all
[*]If 'Soft blocked: yes' and 'Hard blocked: no' then run: rfkill unblock wifi
[*]sudo rfkill list all
[*]sudo ifconfig wlan0 up            -------> wlan0 if that is your wireless device in iwconfig.
[/LIST]

---

### Post by grimey44 on 2011-08-19
i have hardware and software blocked.
maybe my wifi switch actually broke.

---

### Post by chili555 on 2011-08-22
If you can't get 'hard blocked yes' to change by any means whatever, I am not sure there is much else we can do. Have you tried booting with the switch held down? Is there any message if you manipulate the switch and run:```
sudo tail -f /var/log/syslog
```Does the system even recognize the switch movement at all? If so, what are the messages?

You can get out of syslog with Ctrl+c.

---

### Post by meitetsuman on 2012-01-08
I was getting the "wireless disabled by hardware switch" message on my Dell Inspiron laptop. I tried many fixes, but what finally worked was booting up in Windows and then pressing the Fn and F2 keys at the same time. This is apparently the wireless "hardware switch" on these computers. Then I rebooted into Ubuntu and my wireless was working again! :)

---

### Post by EvilRick on 2012-01-11
I have a DV7T-2000 and noticed that the wireless button worked just fine with Ubuntu 10.04 but when I tried 11.10 my wirelss was always "disabled by hardware switch".  And since I dual boot, wireless was disabled in Windows . . . until I reset the BIOS.

Ubuntu 11.10 has 'hp-wmi' loading and 10.04 does not.

**FIX:**

- Open a terminal and input the following commands
```
sudo -s
echo "blacklist hp_wmi" >> /etc/modprobe.d/blacklist.conf
```

- Reboot and go into the BIOS and reset to the default settings.  You can change whatever settings you want back to what you had, but you have to reset to the defaults first.  This re-enables your wireless

- Boot back into Ubuntu and your switch should now be blue instead of orange

*NOTE* I have not tried to turn wireless off with the button but I would imagine if you do, you may have to reboot and/or try the BIOS reset to get it back to normal.  I'm hoping by just blacklisting 'hp-wmi' it will work as normal, but who knows.

---

