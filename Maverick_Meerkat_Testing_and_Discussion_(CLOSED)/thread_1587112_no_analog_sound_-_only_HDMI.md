---
title: "no analog sound - only HDMI"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Tomy on 2010-10-03
I have a new MSI 890GXM-G65 motherboard that has both HDMI and 6 in 1 audio jacks. The HDMI sound is being detected but not the analog.

Sound Preferences-Hardware has this:
RS880 Audio Device [Radeon HD 4200]
1 Output
Digital Stereo (HDMI) Output

On a slightly older MSI motherboard with both HDMI and analog audio there is another entry in the "Hardware" and "Output" sections to select the 5.1 channel analog audio.

alsamixer also shows only "Card: HDA ATI HDMI"

I assume some driver is missing. How can I fix this?

Thanks

---

### Post by Sandsound on 2010-10-03
Not sure if this is what you are looking for, but I just blacklist my HDMI in /etc/modprobe.d/blacklist.conf file.

EDIT:
$ sudo echo blacklist snd_hda_intel >> /etc/modprobe.d/blacklist.conf

---

### Post by Tomy on 2010-10-03
Thanks, I'll give it a try.

---

### Post by Tomy on 2010-10-03
> **Sandsound said:**
> Not sure if this is what you are looking for, but I just blacklist my HDMI in /etc/modprobe.d/blacklist.conf file.

EDIT:
$ sudo echo blacklist snd_hda_intel >> /etc/modprobe.d/blacklist.conf

ok, I tried this in maverick and it did delete the HDMI but I thought that snd_hda_intel might also be needed for the analog card so I tried it in lucid also ( on the same motherboard ).

b4 blacklist (from alsamixer) -- lucid
[FONT=Courier New]&#9484;&#9472;&#9472;&#9472;&#9472;&#9472; Sound Card &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; 
&#9474;   (default)           &#9474;
&#9474;0  HDA ATI SB          &#9474;
&#9474;1  Monitor Webcam      &#9474;
&#9474;2  HDA ATI HDMI        &#9474;
&#9474;   enter device name...&#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

[/FONT] after blacklist only the webcam card was left -- both HDA ATI entries were gone and sound did not work. 

So, this didn't work and I deleted the blacklist line in maverick.

---

### Post by Tomy on 2010-10-03
problem solved

I added ubuntu-audio-dev PPA from here:
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa")

and installed some new alsa-drive-modules.

Actually, here is where the instructions are:
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

### Post by jimbob on 2010-10-03
Post removed.

---

### Post by coibyxqx on 2010-10-05
Thanks, I'll try.

---

