---
title: "acer 5220 laptop microphone not working"
date: 2009-06-18
forum: Multimedia Software
---

### Post by bobdobbs on 2009-06-18
Hi.
I've been using ubuntu for a couple of years now, and I haven't been able to get microphone working on my laptop.

The laptop is an acer extensa 5220.

Under windows, the mic works fine.

If I make a test call with skype, I hear no sound, no matter what I set the input device to.


Googling around, I can see that other people have gotten the mic to work successfully.

In the gnome volume control, mic boost is set to max.

If, between recording tests on gnome-sound-recorder, I go back to Colume Control and switch between capture options ('mic' and 'inbuilt mic') I get either clicking or fuzz and clicking.

How can I enable the mic ?

---

### Post by bobdobbs on 2009-06-19
bump

---

### Post by MZBKA on 2009-06-23
I've been having the same problem.

---

### Post by MZBKA on 2009-06-23
Edit:  My machine is a 4420 though.  I've fooled around with all of the alsa mixer settings and nothing works.  Even for regular audio all of the settings have to be almost maxed out to get a reasonable volume.  If I max out all of the mic settings, I can hear a recording of me tapping on the mic very loudly, but that's it.

Mic works in windows, so that's not the problem.

Please help.  I can't find the solution anywhere online.

---

### Post by MZBKA on 2009-06-24
I've found this:
[https://bugs.launchpad.net/ubuntu/+bug/269294](https://bugs.launchpad.net/ubuntu/+bug/269294)
Towards the bottom a user named THE MIKE suggests downloading a new driver here:
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
However, I can't get this file to "make".  Can anybody help?

---

### Post by xc3RnbFO8P on 2009-06-24
Did you do:
> sudo apt-get install build-essential

---

### Post by MZBKA on 2009-06-24
> **Ringi said:**
> Did you do:

I have now and that has not fixed the problem.

---

### Post by xc3RnbFO8P on 2009-06-24
Extract (Desktop)
> cd  /home/your folder/Desktop/alsa-driver-1.0.20
> ./configure 
> make 
> sudo make install

---

### Post by MZBKA on 2009-06-25
After I try to configure I get
> 
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).


What should I do from here?

Thanks for your help!

---

### Post by xc3RnbFO8P on 2009-06-25
> sudo apt&#8722;get install build&#8722;essential linux&#8722;headers&#8722;$(uname &#8722;r)
and try again.

---

### Post by MZBKA on 2009-06-25
I get
>  build essential is already the newest version

I still have the same problems:  All levels in alsa mixer have to be very high to hear any audio, and even with mic boost, front mic boost, and capture all the way up, almost nothing can be recorded.  Here is some more info that may be useful

> . . .$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: SB [HDA ATI SB], Gerät 0: ALC268 Analog [ALC268 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

(I'm obviously running the German version)

My soundcard is
>    	 	 	 	 	 	  [FONT=Courier New, monospace]00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) [/FONT] 
 [FONT=Courier New, monospace]	Subsystem: Acer Incorporated [ALI] Device 0123 [/FONT] 
 [FONT=Courier New, monospace]	Flags: bus master, slow devsel, latency 64, IRQ 10 [/FONT] 
 [FONT=Courier New, monospace]	Memory at f0700000 (64-bit, non-prefetchable) [size=16K] [/FONT] 
 [FONT=Courier New, monospace]	Capabilities: <access denied> [/FONT] 
 [FONT=Courier New, monospace]	Kernel modules: snd-hda-intel[/FONT]

---

### Post by xc3RnbFO8P on 2009-06-25
Try this:
> ./configure
&#8722;&#8722;with&#8722;kernel=/usr/src/linux&#8722;headers&#8722;$(uname &#8722;r) &#8722;&#8722;with&#8722;cards=ALC268

---

### Post by MZBKA on 2009-06-25
> **Ringi said:**
> Try this:

Here's what I got back
> 
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...


I've done a restart and I still have the same problems.

---

### Post by xc3RnbFO8P on 2009-06-25
I have edit my post #12

---

### Post by MZBKA on 2009-06-25
> **Ringi said:**
> I have edit my post #12

I have been fooling around with different entries for 15 minutes. . .I keep getting the same response:

> 
...$ ./configure&#8722;&#8722;with&#8722;kernel=/usr/src/linux&#8722;headers&#8722;$(uname&#8722;r)&#8722;&#8722;with&#8722;cards=ALC268 

bash: uname&#8722;r: command not found
bash: ./configure&#8722;&#8722;with&#8722;kernel=/usr/src/linux&#8722;headers&#8722;&#8722;&#8722;with&#8722;cards=ALC268: No such file or directory

Am I missing something?

---

### Post by xc3RnbFO8P on 2009-06-25
Just copy/paste 
> ./configure
&#8722;&#8722;with&#8722;kernel=/usr/src/linux&#8722;headers&#8722;$(uname &#8722;r) &#8722;&#8722;with&#8722;cards=ALC268 
you got
> [COLOR="Red"]./configure&#8722;&#8722;with&#8722;kernel=/usr/src/linux&#8722;headers&#8722;&#8722;&#8722;with&#8722;cards=ALC268[/COLOR]

---

### Post by MZBKA on 2009-06-25
Here is exactly what I input and what it returns:

INPUT
```
./configure&#8722;&#8722;with&#8722;kernel=/usr/src/linux&#8722;headers&#8722;$(uname&#8722;r)&#8722;&#8722;with&#8722;cards=ALC268
```This is different from what you asked me to copy in paste in that there is no space between** "uname" and "-r" **and also no space between **"r)" and "--with-cards"**.  I also could not copy and paste what you said because there is an "enter" after "./configure" in your quote.  Here is what I get back:

OUTPUT
> bash: uname&#8722;r: command not found
bash: ./configure&#8722;&#8722;with&#8722;kernel=/usr/src/linux&#8722;headers&#8722;&#8722;&#8722;with&#8722;cards=ALC268: No such file or directory

Edit: If I keep the spaces bolded above,  I get this back
OUTPUT
> uname: zusätzlicher Operand &#8222;&#8722;r&#8220;
&#8222;uname --help&#8220; gibt weitere Informationen.
bash: ./configure&#8722;&#8722;with&#8722;kernel=/usr/src/linux&#8722;headers&#8722;: No such file or directory


---

### Post by xc3RnbFO8P on 2009-06-25
Try this:
> ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)

---

### Post by MZBKA on 2009-06-25
> **Ringi said:**
> Try this:

Here is the tried input and output  with spaces in different places.  The first is the cut and paste.  I'm a total noob, so I have no idea what we're trying to do, but thank you so much for being so patient with me!

```
mzbka@mzbka-laptop:~$ ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
bash: ./configure: No such file or directory

mzbka@mzbka-laptop:~$ ./configure--with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
bash: ./configure--with-cards=hda-intel: No such file or directory

mzbka@mzbka-laptop:~$ ./configure--with-cards=hda-intel--with-kernel=/usr/src/linux-headers-$(uname -r)
bash: ./configure--with-cards=hda-intel--with-kernel=/usr/src/linux-headers-2.6.30-2-generic: No such file or directory

```

---

### Post by MZBKA on 2009-06-26
Please anybody feel free to send me a private message or an instant message to help me fix this.  If I'm spending way too much time trying to get this thing to work.  I'll have to go back to windows if there isn't a solution for this.  Thanks for any help.

---

### Post by MZBKA on 2009-06-26
I should add that neither the interal mic nor my plug in mic works.  Help please!  I don't want to go back to windows!

---

### Post by MZBKA on 2009-06-30
Hey.  I've found a solution here (German):[http://forum.ubuntuusers.de/topic/acer-extensa-5220-soundausgabe-deutlich-leise/](http://forum.ubuntuusers.de/topic/acer-extensa-5220-soundausgabe-deutlich-leise/)

Neither my internal mic nor Skype work, but at least the sound is better and ubuntu functions with a plugged in mic.

Solution:
Open a terminal and enter
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Then add the following as the last line in in your text editor:
```
options snd-hda-intel model=acer
```

---

### Post by bobdobbs on 2009-07-02
Hi guys.

I finally got it working, thanks to the detailed walkthrough on the launchpad page:

[https://bugs.launchpad.net/ubuntu/+bug/269294/comments/57](https://bugs.launchpad.net/ubuntu/+bug/269294/comments/57)

The link was also given by one of the contributers to this thread.

I did not pass any options to configure.
Nor did I use Checkinstall.

Thanks all.

---

### Post by dinoamino on 2009-07-12
> **bobdobbs said:**
> Hi guys.

I finally got it working, thanks to the detailed walkthrough on the launchpad page:

[https://bugs.launchpad.net/ubuntu/+bug/269294/comments/57](https://bugs.launchpad.net/ubuntu/+bug/269294/comments/57)

The link was also given by one of the contributers to this thread.

I did not pass any options to configure.
Nor did I use Checkinstall.

Thanks all.


I'd like to share my experience - a derivative solution to getting the acer microphone working on my laptop.

I use Debian squeeze/testing with a vanilla kernel: 2.6.29.6 x86_64 GNU/Linux

I used the instructions from the link above to create -** but did not install** - an alsa-drivers deb package using checkinstall. I then compared the snd_hda_intel.ko module in the package with the currently running module from my kernel. They were equivalent.

Instead of installing the package I just modified 
*/etc/modprobe.d/alsa-base.conf* and added the following lines to the end of the file

```
alias snd-card-0 snd-hda-intel
 options snd-hda-intel model=acer 
```... and now the internal microphone on my acer laptop finally works in linux!!!

---

### Post by bobdobbs on 2009-07-14
> **dinoamino said:**
> I'd like to share my experience - a derivative solution to getting the acer microphone working on my laptop.

I use Debian squeeze/testing with a vanilla kernel: 2.6.29.6 x86_64 GNU/Linux

I used the instructions from the link above to create -** but did not install** - an alsa-drivers deb package using checkinstall. I then compared the snd_hda_intel.ko module in the package with the currently running module from my kernel. They were equivalent.

Instead of installing the package I just modified 
*/etc/modprobe.d/alsa-base.conf* and added the following lines to the end of the file

```
alias snd-card-0 snd-hda-intel
 options snd-hda-intel model=acer 
```... and now the internal microphone on my acer laptop finally works in linux!!!

Just adding those lines didn't work for me.
I had to go ahead and actually install the new drivers as well as add those lines.

As if to confirm this, my solution stopped working when I automatically updated the kernel with apt-get.

So every time the kernel has to be updated, I have to go through the process again. (Along with re-installing madwifi).

It's not a perfect solution, but it works.

---

