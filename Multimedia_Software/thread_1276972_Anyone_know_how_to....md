---
title: "Anyone know how to..."
date: 2009-09-27
forum: Multimedia Software
---

### Post by sydbat on 2009-09-27
...convert Sony's .dvf audio files to something usable without Windows involvement?

A friend sent me a couple of audio files he recorded with his Sony audio recorder and they are in .dvf format. Any converters available to change them into .wav, .mp3, .etc?

Also, anyone use a Sony audio recorder? Other than the obvious Linux incompatibility, are they any good?

Thanks.

---

### Post by toupeiro on 2009-09-27
> **sydbat said:**
> ...convert Sony's .dvf audio files to something usable without Windows involvement?

A friend sent me a couple of audio files he recorded with his Sony audio recorder and they are in .dvf format. Any converters available to change them into .wav, .mp3, .etc?

Also, anyone use a Sony audio recorder? Other than the obvious Linux incompatibility, are they any good?

Thanks.

Have you tried Audacity?

---

### Post by sydbat on 2009-09-27
> **toupeiro said:**
> Have you tried Audacity?Yup. Won't play for me...but I might be missing a codec or plugin. Does Audacity have some type of converter for .dvf?

---

### Post by toupeiro on 2009-09-27
> **sydbat said:**
> Yup. Won't play for me...but I might be missing a codec or plugin. Does Audacity have some type of converter for .dvf?

I didn't research too deeply, but I did google around for a few minutes and found a few hits of people telling other people to try Audacity.  I was just going for a quick win here. :)  Sorry it wasn't too helpful.

---

### Post by sydbat on 2009-09-27
> **toupeiro said:**
> I didn't research too deeply, but I did google around for a few minutes and found a few hits of people telling other people to try Audacity.  I was just going for a quick win here. :)  Sorry it wasn't too helpful.Well, I'm looking on the Audacity site now for a plugin. If I find one, I'll let everyone know! If not...

---

### Post by JMMR on 2010-11-10
I figured out how to convert these files (DVF) under Linux.  It is a pain.  My wife bought the Sony ICD-SX46 (Which is no longer under support, and works only on WinXP) a while back.  I had to install VirtualBox, Windows XP to extract the files to the HDD, and move them to my main drive under Linux Mint.

At any rate, You will have to go to Sony's Support Page and download the [Digital Voice Editor 3]("http://esupport.sony.com/perl/swu-download.pl?upd_id=5529&SMB=YES&template_id=1&region_id=1"), then install it via WINE.  **Now, it will give some errors (Don't worry) as this program does not work under wine correctly, but that is irrelevant to what we want to do.**  **This program will not have play back capabilities under wine!**  You will need to locate the folder under the *PC* dialog window/section, and the file in the dialog section under the *PC* section.  Select the file, when you click on it, it will give an error, just click OK.  The file will be highlighted now, click on PC>Conver_t_ MP3... (This is the menu area where _F_ile, _E_dit, &c., is located at the top).  Let it convert the file, from there you can use audacity to convert it further if needed.  The converted file will be located in the same folder as the original.

[B]NOTE:  You will need to load the program manually as the link in the menu doesn't seem to work properly.  The File is located:
./wine/dosdevices/c:/Program Files/SONY/Digital Voice Editor 3/DVEdit.exe
Update:  The Desktop Icon (Shortcut) Seems to work
[/B]

---

### Post by eeBus on 2012-03-05
Wow! Worked for me! Thanks for the instructions!

---

### Post by oldos2er on 2012-03-05
Closed, necromancy.

---

