---
title: "Sound Problem in Acer 4930"
date: 2011-01-27
forum: Multimedia Software
---

### Post by gubbaraviteja on 2011-01-27
Hello Everyone,
I am new to Ubuntu and i have just installed Ubuntu 10.10 in my acer laptop (4930 series) but the problem is there is no sound.
I have multiple operating systems in my laptop with windows7 as another OS.
When I first booted to windows7 and again restarted to Ubuntu I am getting sound. But when directly booted to Ubuntu there is no sound.
I hope my sound card is not getting detected while I choose Ubuntu when I power on my laptop. And when I choose windows7 when I power on my laptop and then switched to Ubuntu I am getting sound.
I hope you got the point and please help me to get rid of this problem.

Contact me @ [email]gubbaraviteja@gmail.com[/email]

---

### Post by lidex on 2011-01-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by gubbaraviteja on 2011-01-31
Hello lidex,
Thank you for your help and when run that script it finally said "your ALSA information is located at 

"http://www.alsa-project.org/db/?f=41abbd86e5383ecee3c8d18571fa2c1db2de3805"

---

### Post by lidex on 2011-01-31
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=acer-aspire-4930g" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by gubbaraviteja on 2011-02-09
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=acer-aspire-4930g" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
Hello lidex,
Thank you for your help. When I tried the code it terminal it showed 

raviteja@raviteja-Aspire-4930:~$ echo "options snd-hda-intel model=acer-aspire-4930g" | sudo tee -a /etc/modprobe.d/alsa-base.conf
[sudo] password for raviteja: 
options snd-hda-intel model=acer-aspire-4930g
raviteja@raviteja-Aspire-4930:~$ 

But there is no sound yet.
Is there something I should do more.

---

### Post by lidex on 2011-02-09
> **gubbaraviteja said:**
> Hello lidex,
Thank you for your help. When I tried the code it terminal it showed 

raviteja@raviteja-Aspire-4930:~$ echo "options snd-hda-intel model=acer-aspire-4930g" | sudo tee -a /etc/modprobe.d/alsa-base.conf
[sudo] password for raviteja: 
options snd-hda-intel model=acer-aspire-4930g
raviteja@raviteja-Aspire-4930:~$ 

But there is no sound yet.
Is there something I should do more.

You of course need to reboot then check your settings/configuration:
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

