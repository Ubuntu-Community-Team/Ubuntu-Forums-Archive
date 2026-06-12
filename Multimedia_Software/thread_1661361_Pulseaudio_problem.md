---
title: "Pulseaudio problem"
date: 2011-01-06
forum: Multimedia Software
---

### Post by lt_y3k on 2011-01-06
I get the error "Assertion 'o' failed at pulse/operation.c:128, function pa_operation_get_state(). Aborting." while playing iptv through Tano or videos  through vlc, when i get this error sound disappears in player.
OS: Ubuntu Linux 2.6.35-24-generic x86_64
VLC version: 1.1.4 The Luggage
Tano version: 0.7.3

---

### Post by gordintoronto on 2011-01-06
What sound card?  Running Accessories/Terminal and entering the command "lspci" should identify your sound card.

---

### Post by lidex on 2011-01-07
Reset your pulse configuration:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**
Now run this command and post the terminal output:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by lt_y3k on 2011-01-09
Sound card: 03:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

---

### Post by lt_y3k on 2011-01-09
> **lidex said:**
> Reset your pulse configuration:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```**Logout/in.**
Now run this command and post the terminal output:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

rm: cannot remove `/home/xxx/.asound*': No such file or directory
independent@admin:~$ rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
rm: cannot remove `/home/xxx/.pulse': No such file or directory
rm: cannot remove `/home/xxx/.asound*': No such file or directory
rm: cannot remove `/home/xxx/.pulse-cookie': No such file or directory
independent@admin:~$ sudo rm /etc/asound.conf
rm: cannot remove `/etc/asound.conf': No such file or directory

---

### Post by lidex on 2011-01-09
So no pulse then?

---

### Post by lt_y3k on 2011-01-10
No, i use pulse audio.

---

### Post by lidex on 2011-01-11
> **lt_y3k said:**
> No, i use pulse audio.
Then you need to re-install it.

---

### Post by lt_y3k on 2011-01-11
I reinstalled ubuntu and have same problem...

---

### Post by lidex on 2011-01-13
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by lt_y3k on 2011-01-13
I attached the output file.

---

### Post by lidex on 2011-01-13
That all looks fine. After the re-install you still have the problem? And just with the two players you mention? I am not familiar with tano, but in vlc what do you have chosen as your audio output module?

---

### Post by xcristi on 2011-01-21
I had also the same problem after an update.

After checking the speakers and so, I took a look at Pulseaudio Control:

[IMG]http://img713.imageshack.us/img713/8762/75981192.png[/IMG]

and see that nothing is muted and I got some activity in that thin status bar.

Then, in Multimedia->Mixer

[IMG]http://img23.imageshack.us/img23/1232/36682898.png[/IMG]

check for Switches ( IEC958 ) to be **unchecked**.

Now the sound is back. ;)

---

### Post by lt_y3k on 2011-01-21
> **xcristi said:**
> I had also the same problem after an update.

After checking the speakers and so, I took a look at Pulseaudio Control:

[IMG]http://img713.imageshack.us/img713/8762/75981192.png[/IMG]

and see that nothing is muted and I got some activity in that thin status bar.

Then, in Multimedia->Mixer

[IMG]http://img23.imageshack.us/img23/1232/36682898.png[/IMG]

check for Switches ( IEC958 ) to be **unchecked**.

Now the sound is back. ;)

It is unchecked already.

---

### Post by Siechtum on 2011-01-25
I have this problem too.

I just updated from Mint 9 64 Bit to Mint 10.

I also use the same soundcard.

when I use vlc (or any other movie player for that matter) I get this error message:

Assertion 'o' failed at pulse/operation.c:128, function pa_operation_get_state(). Aborting.

and pulseaudio restarts and vlc crashes. I never had problems with pulseaudio with 32 bit Mint 9.

PS: I updated to 64 bit because of a new PC with 4 GB of RAM

edit: Seems there is a bug in the 64 bit driver for the SB Audigy LS. I enabled my on board sound device and 5.1 sound runs fine.

---

### Post by lt_y3k on 2011-01-26
Yes, i think that it is a bug, because i now use motherboards audio card and problem is gone :) so i have to tag this post as solved? And where can i notify about this bug?

---

### Post by Siechtum on 2011-01-26
No. Its not solved. And I think a bug for this is already filed. (but I gonna look into this again).

---

### Post by lt_y3k on 2011-01-27
Yes, this sound card :)

---

### Post by lidex on 2011-01-27
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

