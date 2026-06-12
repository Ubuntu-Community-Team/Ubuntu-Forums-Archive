---
title: "No Sound Acer Aspire One"
date: 2011-07-07
forum: Multimedia Software
---

### Post by spacetimecowboy on 2011-07-07
Hello lovely people!

My sound totally disappeared for no reason I can see. I did no upgrades, updates, fiddling.


I updated from 9.10 to 10.4. No joy.


I followed the instructions given in the **Comprehensive Sound Problem Solutions Guide  ** [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449).

My sound card is detected and running. All levels in the alsa mixer are sweet as far as I can tell

Changed settings at

```

[SIZE=2]grep 'audio' /etc/group[/SIZE]

```from

```

[SIZE=2]audio:x:29:pulse[/SIZE]

```to

```

[SIZE=2]audio:x:29:tom[/SIZE]

```(my username)

No joy.


Any ideas?

Thank you for your kind attention.

---

### Post by lidex on 2011-07-08
You can add yourself to that group but you don't want to remove pulse so put it back. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by spacetimecowboy on 2011-07-09
Hi,

Thanks for your patience.

I spent a whole day trying to connect to the alsa site, but every single time the connection timed out or was reset by peer. I have a decent internet connection so I don't understand. Also, [www.alsa-project.org](www.alsa-project.org) does not open in my browser.

I returned pulse to the group.

Sorry I don't seem to be able to access that useful information.

Any ideas?

Thanks

---

### Post by lidex on 2011-07-09
The server must be down. I'll attach the script to this post. Extract into your /home/user folder. Run the script using this format:
```
bash alsa-info.sh --no-upload
```
Upload the resulting textfile from your /tmp directory as an attachment

---

### Post by spacetimecowboy on 2011-07-10
Hi Lidex,

I opened it with the archive manager and saved it locally. Opened the text file containing the script.

The resulting file is named gedit.tom.2724049638 but contains 0 bytes and cannot be opened my end or uploaded.

Maybe I am doing something incorrectly?

---

### Post by lidex on 2011-07-10
> **spacetimecowboy said:**
> Hi Lidex,

I opened it with the archive manager and saved it locally. Opened the text file containing the script.

The resulting file is named gedit.tom.2724049638 but contains 0 bytes and cannot be opened my end or uploaded.

Maybe I am doing something incorrectly?

Extract it to your /home/user folder. Then run this command:
```
bash alsa-info.sh
```

---

### Post by spacetimecowboy on 2011-07-10
Hey, please excuse my ignorance, but what next?

```

ALSA Information Script v 0.4.58
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

```I don't know how to access the diagnostics or even the command line options mentioned.

Thanks for your help

---

### Post by lidex on 2011-07-10
Try this format:
```
bash alsa-info.sh --no-upload
```

---

### Post by spacetimecowboy on 2011-07-10
Great, it worked.

Here is the info.

Also, I have discovered that sound is working from the headphone socket.

Thanks.

---

### Post by lidex on 2011-07-10
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=acer-aspire" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by spacetimecowboy on 2011-07-10
returned;

```

options snd-hda-intel model=acer-aspire

```

---

### Post by spacetimecowboy on 2011-07-17
Bump.

```

^?tom@Toms-Little-Badger:~$ echo "options snd-hda-intel model=acer-aspire" | sudtee -a /etc/modprobe.d/alsa-base.conf
[sudo] password for tom: 
options snd-hda-intel model=acer-aspire
tom@Toms-Little-Badger:~$ 

```

(Toms-Little-Badger is the CPU name)

Any ideas?

---

### Post by lidex on 2011-07-17
> **spacetimecowboy said:**
> Bump.

```

^?tom@Toms-Little-Badger:~$ echo "options snd-hda-intel model=acer-aspire" | sudtee -a /etc/modprobe.d/alsa-base.conf
[sudo] password for tom: 
options snd-hda-intel model=acer-aspire
tom@Toms-Little-Badger:~$ 

```

(Toms-Little-Badger is the CPU name)

Any ideas?

Post an updated alsa-info output please.

---

### Post by spacetimecowboy on 2011-07-17
Thanks Lidex

---

### Post by lidex on 2011-07-17
Looks fine other than not a lot of mixer controls. Try these different models:
```
acer
acer-dmic
auto
```
Now you'll have to manually remove the previous entry, which you managed to get in there twice. So remove one line and edit the other, just changing the model name. Reload alsa after each change and check your mixer and sound preference settings.
Edit:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Reload:
```
sudo alsa force-reload
```

---

### Post by spacetimecowboy on 2011-10-10
Hello Lidex,

I have been unable to use my computer for some time but am now back into it.

I left your last reply hanging because I didn't really understand it and I found that the headphones work, but I would now really like to try and resolve the sound issues.

Since then I have had a complete wipe and reinstall, now running 10.04 without partition, but the issue persists. I bought some usb speakers (power and data both via usb) which won't work.

If you could help me, as if I was a 5 year old who knew little about computers, I would be very grateful.

Thanks in advance for your patience and assistance.

.

---

### Post by lidex on 2011-10-10
You could start with an updated alsa-info.txt

---

### Post by spacetimecowboy on 2011-10-11
.

---

### Post by spacetimecowboy on 2011-10-11
Also here is the current alsa base, I am not sure what changes you were suggesting.

---

