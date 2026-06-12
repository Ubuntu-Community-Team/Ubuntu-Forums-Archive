---
title: "[SOLVED] Gutsy Firefox Flash no sound"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by cotcot on 2007-10-25
EDIT :: SOLVED

I have gutsy on amd64 with firefox. Sound is working normal except for firefox/flash. Opening a video (like youtube) makes the video playing without sound.I have tried the ff32-3in1 as well but no succes.
With feisty on the same desktop (other hdd) it is working well.
I have sun-java6-jre sun-java6-bin and flashplugin-nonfree installed.

EDIT : I found out that i get sound with a youtube video when I run firefox as root. 

Any ideas what is wrong ?

---

### Post by undadecor on 2007-10-25
Try 
```
killall esd
```
with the browser and all programs shutdown.

[Take a look at this thread]("http://ubuntuforums.org/showthread.php?p=1174435")

---

### Post by cotcot on 2007-10-25
Thanks for replying undadecor.
I tried (killall esd) your suggestion but no sound.
I added a new user and sound is working for the new user. At least this gives me a work around.

---

### Post by newton64 on 2007-10-25
> **cotcot said:**
> Thanks for replying undadecor.
I tried (killall esd) your suggestion but no sound.
I added a new user and sound is working for the new user. At least this gives me a work around.

Hey, I had the same exact problem as you...Flash sound wouldn't work in Firefox, though every other type of sound (mp3, wav, etc.) was doing fine...

I found my answer at post #5 [here]("http://ubuntuforums.org/showthread.php?p=3446685"). Long story short:

```
 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old
```

Then restart Firefox, and in my case YouTube was workin' fine. Hope you get the same results.

---

### Post by cotcot on 2007-10-26
Thanks for your solution newton64. It solved the problem.
I had the asound and asound.conf files from feisty. As my home directory is on a separate partition it was not changed when I installed gutsy with only the root partition reformatted.

---

### Post by m61 on 2007-10-28
i am also having the same problem...the two move commands do not work as i do not have the two files...and when i run FF as root i see this when i try to view a youtube video
```
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
```

anyone got a fix for that?

[all other sound is fine, just not flash]

---

### Post by FarJumper on 2007-10-28
I have the same. Maybe something useful will be posted here:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/150129](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/150129)

---

### Post by tvphil on 2007-10-31
None of these ideas worked for me, but I found one that does. First, go to Synaptic and download all of the Pulse Audio packages, including libpulse-dev,build-essential, libsed0-dev, and libssl-dev. You'll need all that for what I will tell you to do. Pulse Audio is not installed by default, but I believe it should be for this problem alone. It picks up where ESD leaves off. If you have problems hearing your system sounds, pulse audio will help that too. Next, click on the following link to get the tarball you need to install, to get audio in Flash to work.
[https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/Tarballs/libflashsupport-1.2.tar.bz2](https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/Tarballs/libflashsupport-1.2.tar.bz2)
Open with 'file-roller" default and extract this to your home folder. Next in a terminal, type the words "cd libflashsupport-1.2", then hit enter key.. Then simply type the words "make sudoinstall" and hit the enter key again and type your password in when it prompts you to, hit enter again. Finally, click out of the terminal, open Firefox and go to Youtube or any other place that has a flash video, you should be able to hear it now. Sorry about the compile 101 jargon, I just want to make sure any Ubuntu newbie can do this and maybe learn something in the process. One more thing to mention, the link I supplied is from the pulseaudio.org website. It's very hard navigating to where this link is on their website, so I made it easier.

---

### Post by brk3 on 2007-11-01
that worked for me, cheers

---

### Post by ubukool on 2007-11-01
Hi everyone,

You might want to try this, it worked for me!  Nice and easy:

[http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/)

Good luck :)

---

### Post by clean97gti on 2007-11-04
ubukool, this worked for me. Good lookin out. :)

---

### Post by StevenHarper on 2007-11-05
> **newton64 said:**
> Hey, I had the same exact problem as you...Flash sound wouldn't work in Firefox, though every other type of sound (mp3, wav, etc.) was doing fine...

I found my answer at post #5 [here]("http://ubuntuforums.org/showthread.php?p=3446685"). Long story short:

```
 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old
```

Then restart Firefox, and in my case YouTube was workin' fine. Hope you get the same results.

This worked for me : I upgraded from Feisty, I bet thats what caused it

thanks for the handy info

Steve

---

### Post by pthivent on 2007-11-07
> **ubukool said:**
> Hi everyone,

You might want to try this, it worked for me!  Nice and easy:

[http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/)

Good luck :)

It worked for me too. AWESOME!

---

### Post by JustAboutRealJAR on 2007-11-09
> **tvphil said:**
> None of these ideas worked for me, but I found one that does. First, go to Synaptic and download all of the Pulse Audio packages, including libpulse-dev,build-essential, libsed0-dev, and libssl-dev. You'll need all that for what I will tell you to do. Pulse Audio is not installed by default, but I believe it should be for this problem alone. It picks up where ESD leaves off. If you have problems hearing your system sounds, pulse audio will help that too. Next, click on the following link to get the tarball you need to install, to get audio in Flash to work.
[https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/Tarballs/libflashsupport-1.2.tar.bz2](https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/Tarballs/libflashsupport-1.2.tar.bz2)
Open with 'file-roller" default and extract this to your home folder. Next in a terminal, type the words "cd libflashsupport-1.2", then hit enter key.. Then simply type the words "make sudoinstall" and hit the enter key again and type your password in when it prompts you to, hit enter again. Finally, click out of the terminal, open Firefox and go to Youtube or any other place that has a flash video, you should be able to hear it now. Sorry about the compile 101 jargon, I just want to make sure any Ubuntu newbie can do this and maybe learn something in the process. One more thing to mention, the link I supplied is from the pulseaudio.org website. It's very hard navigating to where this link is on their website, so I made it easier.

note: libsed0-dev should be **libesd0-dev**

---

### Post by z0mbie on 2007-11-09
Didn't work for me guys :[ 

PulseAudio ?

---

### Post by DaveTRG on 2007-11-11
This is what I get when trying to compile libflashsupport on Gutsy amd64:

```
dave@computer02:~/Desktop/libflashsupport-1.2$ make sudoinstall
gcc -fPIC -shared -O2 -Wall -Werror  -lpthread -DLIBDIR=/usr/lib \
        -DALSA_INTERNAL  -DPULSEAUDIO -DLIBPULSEPATH='"/usr/lib/libpulse-simple.so.0"' -DESD -DLIBESDPATH='"/usr/lib/libesd.so.0"' \
        -DOSS -DOPENSSL -lssl  \
        flashsupport.c -o libflashsupport.so
cc1: warnings being treated as errors
flashsupport.c: In function ‘FPX_SoundOutput_Open’:
flashsupport.c:502: warning: cast from pointer to integer of different size
flashsupport.c:514: warning: cast from pointer to integer of different size
flashsupport.c:544: warning: cast from pointer to integer of different size
make: *** [libflashsupport.so] Error 1
```

Any help is greatly appreciated.  None of the solutions that I have tried has fixed flash sound in Firefox...

---

### Post by Seamless in Northampton on 2007-11-11
I too got nothing but errors with the Pulse Audio idea. When I try the .asoundconf method, it tells me there's no such file. 

Now here's the weird thing: I run Ubuntu Studio. I discovered that my FF to GG upgrade only partially upgraded Ubuntu Studio. I finished the upgrade to GG Studio using the method recommended at their site. Bingo! Flash audio!

I rebooted later. No Flash audio! There's room next to me if you need a place to bang your head against the wall...

Any help tremendously appreciated.

---

### Post by gubemton on 2007-11-15
> **tvphil said:**
> None of these ideas worked for me, but I found one that does. First, go to Synaptic and download all of the Pulse Audio packages, including libpulse-dev,build-essential, libsed0-dev, and libssl-dev. You'll need all that for what I will tell you to do. Pulse Audio is not installed by default, but I believe it should be for this problem alone. It picks up where ESD leaves off. If you have problems hearing your system sounds, pulse audio will help that too. Next, click on the following link to get the tarball you need to install, to get audio in Flash to work.
[https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/Tarballs/libflashsupport-1.2.tar.bz2](https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/Tarballs/libflashsupport-1.2.tar.bz2)
Open with 'file-roller" default and extract this to your home folder. Next in a terminal, type the words "cd libflashsupport-1.2", then hit enter key.. Then simply type the words "make sudoinstall" and hit the enter key again and type your password in when it prompts you to, hit enter again. Finally, click out of the terminal, open Firefox and go to Youtube or any other place that has a flash video, you should be able to hear it now. Sorry about the compile 101 jargon, I just want to make sure any Ubuntu newbie can do this and maybe learn something in the process. One more thing to mention, the link I supplied is from the pulseaudio.org website. It's very hard navigating to where this link is on their website, so I made it easier.

Yes, that also worked for me.

You should remember to restart the Pulse Audio server with ```
sudo /etc/init.d/pulseaudio restart
``` or restart the computer after the **make sudoinstall** to let PulseAudio find the recently installed libflashsupport library or Firefox & flash won't work fine (I got no sound and video freezing).

Thank's a lot! :guitar:

---

### Post by gubemton on 2007-11-15
> **DaveTRG said:**
> This is what I get when trying to compile libflashsupport on Gutsy amd64:

```
dave@computer02:~/Desktop/libflashsupport-1.2$ make sudoinstall
gcc -fPIC -shared -O2 -Wall -Werror  -lpthread -DLIBDIR=/usr/lib \
        -DALSA_INTERNAL  -DPULSEAUDIO -DLIBPULSEPATH='"/usr/lib/libpulse-simple.so.0"' -DESD -DLIBESDPATH='"/usr/lib/libesd.so.0"' \
        -DOSS -DOPENSSL -lssl  \
        flashsupport.c -o libflashsupport.so
cc1: warnings being treated as errors
flashsupport.c: In function &#8216;FPX_SoundOutput_Open&#8217;:
flashsupport.c:502: warning: cast from pointer to integer of different size
flashsupport.c:514: warning: cast from pointer to integer of different size
flashsupport.c:544: warning: cast from pointer to integer of different size
make: *** [libflashsupport.so] Error 1
```

Any help is greatly appreciated.  None of the solutions that I have tried has fixed flash sound in Firefox...

It worked fine for me on an x86 (32 bits).

I've looked at the **flashsupport.c** file and the conflicting lines (502, 514, 544) are only debug output, not necessary to run the library.

You can try to comment these lines (putting a double slash before them //) or simply remove them.
Save the modified file and rerun the **make sudoinstall**.

Other option you have is to modify the **Makefile** file in the ~/Desktop/libflashsupport-1.2 directory changing third line from ```
CFLAGS=-fPIC -shared -O2 -Wall -Werror
``` to ```
CFLAGS=-fPIC -shared -O2 -Wall
``` and rerun the **make sudoinstall**.

---

### Post by billybag on 2007-11-22
NONE of these seem to have workedfor me yet. Anyone else still having trouble?

---

### Post by erealz on 2007-11-28
yea im hooking up my cuzin with his amd box creative soundcard with ubuntu install . MP3 PLAYS FINE BUT NO SOUND ON FLASH ON YOUTUBE OR ANYTHING ELSE FALSH THIS BLOW ANYONE HAVE HAVA A FIX

---

### Post by Yellow Pasque on 2007-11-29
For anyone on AMD64 trying to compile libflashsupport for use with the 32-bit Flash plugin, you'll need to comment out the #define OPENSSL line in the flashsupport.c file.

Get gcc 4.1 or better and its corresponding multilib package and compile with the -m32 flag. Example:
```
sudo apt-get install gcc-4.1 gcc4.1-base gcc-4.1-multilib build-essential
cc -shared -O2 -Wall -Werror -m32 -fPIC flashsupport.c -o libflashsupport.so
```

Then put your new libflashsupport.so file in /usr/lib and put symbolic links in /usr/lib32, /usr/lib/firefox/plugins, and /usr/mozilla/plugins

---

### Post by coolbrook on 2007-12-01
> **tvphil said:**
> None of these ideas worked for me, but I found one that does. First, go to Synaptic and download all of the Pulse Audio packages, including libpulse-dev,build-essential, libsed0-dev, and libssl-dev. You'll need all that for what I will tell you to do. Pulse Audio is not installed by default, but I believe it should be for this problem alone. It picks up where ESD leaves off. If you have problems hearing your system sounds, pulse audio will help that too. Next, click on the following link to get the tarball you need to install, to get audio in Flash to work.
[https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/Tarballs/libflashsupport-1.2.tar.bz2](https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/Tarballs/libflashsupport-1.2.tar.bz2)
Open with 'file-roller" default and extract this to your home folder. Next in a terminal, type the words "cd libflashsupport-1.2", then hit enter key.. Then simply type the words "make sudoinstall" and hit the enter key again and type your password in when it prompts you to, hit enter again. Finally, click out of the terminal, open Firefox and go to Youtube or any other place that has a flash video, you should be able to hear it now. Sorry about the compile 101 jargon, I just want to make sure any Ubuntu newbie can do this and maybe learn something in the process. One more thing to mention, the link I supplied is from the pulseaudio.org website. It's very hard navigating to where this link is on their website, so I made it easier.

I didn't reboot until it was suggested but I'm pretty sure it was this fix that did the trick.  Thanks!

:-\"

---

### Post by ctt1wbw on 2007-12-02
Sweetness.  I got the sound in firefox to work again.  How it stopped in the first freakin place is beyond me, but it works now.

I knew I could count on the Ubuntu forums to solve this.  =D>

---

### Post by macabro22 on 2007-12-04
Even Easier way =]

Get the debfile mentioned here! [http://joey.ubuntu-rocks.org/blog/2007/11/18/sound-with-oss-pa-flash/]("http://joey.ubuntu-rocks.org/blog/2007/11/18/sound-with-oss-pa-flash/")

Sweet eh?!

---

### Post by Cazzj on 2007-12-07
I just wanted to tack on my observations with Firefox.  Ever since I upgraded to Gutsy, Firefox has been sucky unstable...and I've been keeping up with updates too.  In addition to the no-sound Flash problem, Firefox either freezes up and I have to kill it, or it quits completely on its own.  :-/

---

### Post by John Azelvandre on 2007-12-08
This doesn't work for me.  I get:

```
mv: cannot stat `/home/zizonus/.asoundrc': No such file or directory
```

Would dearly like to get flash video sound back.  Disappeared after upgrade to Gutsy.

---

### Post by almabeck on 2007-12-10
> **tvphil said:**
> None of these ideas worked for me, but I found one that does. First, go to Synaptic and download all of the Pulse Audio packages, including libpulse-dev,build-essential, libsed0-dev, and libssl-dev. You'll need all that for what I will tell you to do. Pulse Audio is not installed by default, but I believe it should be for this problem alone. It picks up where ESD leaves off. If you have problems hearing your system sounds, pulse audio will help that too. Next, click on the following link to get the tarball you need to install, to get audio in Flash to work.
[https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/Tarballs/libflashsupport-1.2.tar.bz2](https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/Tarballs/libflashsupport-1.2.tar.bz2)
Open with 'file-roller" default and extract this to your home folder. Next in a terminal, type the words "cd libflashsupport-1.2", then hit enter key.. Then simply type the words "make sudoinstall" and hit the enter key again and type your password in when it prompts you to, hit enter again. Finally, click out of the terminal, open Firefox and go to Youtube or any other place that has a flash video, you should be able to hear it now. Sorry about the compile 101 jargon, I just want to make sure any Ubuntu newbie can do this and maybe learn something in the process. One more thing to mention, the link I supplied is from the pulseaudio.org website. It's very hard navigating to where this link is on their website, so I made it easier.

I'm a very new newbie, as will probably be obvious from this post. I think I did what you described, but when I hit enter after "make sudoinstall" I get this message: "make:*** No rule to make target 'sudoinstall'. Stop."
BTW, I have sound when I play a CD, but no sound in Firefox. Can't get my installed microphone to work, either. I have a Dell Inspiron 1420, with Gutsy Gibbon.

Alma

---

### Post by birdywa on 2007-12-16
I am having the same problem with
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
coming up when I run firefox as root. I have tried some of these "fixes", but none have worked. Has anybody come up with a solution to this problem? By the way: I have found firefox to be very buggy and unstable overall in Gutsy, closing randomly all the time.

---

### Post by malachi on 2007-12-18
> **almabeck said:**
> I'm a very new newbie, as will probably be obvious from this post. I think I did what you described, but when I hit enter after "make sudoinstall" I get this message: "make:*** No rule to make target 'sudoinstall'. Stop."
BTW, I have sound when I play a CD, but no sound in Firefox. Can't get my installed microphone to work, either. I have a Dell Inspiron 1420, with Gutsy Gibbon.

Alma

That command should be "sudo make install" rather than what he has. It's not your fault.

---

### Post by techstop on 2007-12-18
I tried installing the deb mentioned earlier in this thread, no go. Then I found this ubuntu documentation article;

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

I installed PulseAudio to fix audio problems with Neverwinter Nights, but I think that is what broke my flash sound. I installed the deb (libflashsupport) from that article, and everything is sweet again.

---

### Post by subordin8 on 2007-12-21
I was having the exact same problem: Audio was working while listening to mp3s etc, but not in Firefox. It turned out that Ubuntu randomly decided that it wasn't sure which of my sound cards to use. So, the way to fix this is to figure out which sound card you want as default and manually set it. NOTE: I went through System/Preferences/Sound and set it all there but to no avail... I had to do it manually.

To see the list of sound cards:
```
sudo asoundconf list
```

To set the default sound card:
```
sudo asoundconf set-default-card <NAME OF CARD AS SHOWN ABOVE>
```

Hope that helps somebody.

---

### Post by ironstorm on 2007-12-26
> **subordin8 said:**
> I was having the exact same problem: Audio was working while listening to mp3s etc, but not in Firefox. It turned out that Ubuntu randomly decided that it wasn't sure which of my sound cards to use. So, the way to fix this is to figure out which sound card you want as default and manually set it. NOTE: I went through System/Preferences/Sound and set it all there but to no avail... I had to do it manually.

To see the list of sound cards:
```
sudo asoundconf list
```

To set the default sound card:
```
sudo asoundconf set-default-card <NAME OF CARD AS SHOWN ABOVE>
```

Hope that helps somebody.

Doesn't work for me...  I only had one sound card to begin with... 

Is there a way to get this working without pulseaudio?   (pulseaudio is impossible to get configured on Kubuntu based on the instructions available - all of which are assuming you have Gnome + esd)

---

### Post by vseehua on 2008-01-04
Installing libflashsupport solved the problem for me as well...

---

### Post by xiphias360 on 2008-01-06
> **malachi said:**
> That command should be "sudo make install" rather than what he has. It's not your fault.

No, make sudoinstall is correct as per the readme and is recommended for 'those with sudo access'.

---

### Post by xiphias360 on 2008-01-06
I tried every single recommendation here and nothing worked. I ended up installing firefox 3 beta 2 and doing a manual flash install with the tar from the adobe site. I tried a few more things from other sites but again nothing worked.

I have a fresh gutsy install, no upgrade. I wiped windows from my laptop and installed gutsy so there's no upgrade issue. I could run firefox as root and hear sound on youtube but not as regular users. After working on this for about 5 hours, i tried my own experiments.

I did an ls -al ~/ and saw that i owned every file except 2, .adobe and .macromedia. Those belonged to root. So i chowned each to my username but still, no sound as a regular user. So then I did mv ~/.adobe ~/.adobe.old and mv ~/.macromedia ~/.macromedia.old and opened up firefox again and now everything works. I doubt having the ff 3 b2 helps so if you have a similar situation try it with ff2 and see what happens. maybe it was a combination of trying every single option i read but my sound is working great and with the ff3 and manual adobe install I don't have the lockup/freezing issues i had before.

---

### Post by war59312 on 2008-01-12
OK audio working fine here in youtube...

that isif your only listening to audio via youtube.com, if othe audio is playing else where then you still get no sound.. seems only 1 audio source is allowed at a time.. sucks!

---

### Post by HairyOaf on 2008-01-12
I've tried every single suggestion in this thread and while I've learnt a great deal about Ubuntu in the process, my Flash sites remain silent :(  Could it be because I'm using Logitech USB speakers? I wouldn't have thought so because they work fine with all my other audio apps. I'm too new to all this Linux stuff to know what else to try without possibly breaking something!

---

### Post by Alyx on 2008-01-12
I had a similar problem but i had no sound totally. I installed libflashsupport and set my audio to multichannel and everything is happy now

---

### Post by tikal26 on 2008-01-15
How to oyu set your audio to multichannel? I get sounds in flash sometiems a, butthen it won;t work int hings like amarok. If I use Amarok flash wont work.

---

### Post by dr.congo on 2008-02-11
I've tried all the fixes on these boards but still no luck, however I've found an odd way to get audio in Flash in Gutsy so I thought I'd add it here in case it helps anyone else.

I've got the Flock browser installed, but the Flash plug-in is not installed for this browser. However, if I start up Flock and browse to a page that should have Flash, then close Flock, then start up Firefox, the audio in Flash works. 

Like I say, it's an odd one.

---

### Post by bfsmith9 on 2008-02-11
Thanks! I'm running Debian testing - had the same problem. Moved  ~/.asoundrc to ~/.asoundrc.old and
~/.asoundrc.asoundconf to ~/.asoundrc.asoundconf.old. Then it worked. Had me stumped all weekend.

---

### Post by Roboticexile on 2008-02-16
> **newton64 said:**
> Hey, I had the same exact problem as you...Flash sound wouldn't work in Firefox, though every other type of sound (mp3, wav, etc.) was doing fine...

I found my answer at post #5 [here]("http://ubuntuforums.org/showthread.php?p=3446685"). Long story short:

```
 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old
```

Then restart Firefox, and in my case YouTube was workin' fine. Hope you get the same results.
 where am i supposed to enter this code? i tried entering it in terminal but i couldn't get it to work, please tell me what i'm doing wrong =]
```
 robert@robert-ubuntu:~$ mv ~/.asoundrc .asoundrc.old
mv: cannot stat `/home/robert/.asoundrc': No such file or directory
robert@robert-ubuntu:~$ mv ~/.asoundrc.asoundconf ~/.asoundconf.old
mv: cannot stat `/home/robert/.asoundrc.asoundconf': No such file or directory 
```

---

### Post by xVehemencityx on 2008-03-03
> **tvphil said:**
> None of these ideas worked for me, but I found one that does. First, go to Synaptic and download all of the Pulse Audio packages, including libpulse-dev,build-essential, libsed0-dev, and libssl-dev. You'll need all that for what I will tell you to do. Pulse Audio is not installed by default, but I believe it should be for this problem alone. It picks up where ESD leaves off. If you have problems hearing your system sounds, pulse audio will help that too. Next, click on the following link to get the tarball you need to install, to get audio in Flash to work.
[https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/Tarballs/libflashsupport-1.2.tar.bz2](https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/Tarballs/libflashsupport-1.2.tar.bz2)
Open with 'file-roller" default and extract this to your home folder. Next in a terminal, type the words "cd libflashsupport-1.2", then hit enter key.. Then simply type the words "make sudoinstall" and hit the enter key again and type your password in when it prompts you to, hit enter again. Finally, click out of the terminal, open Firefox and go to Youtube or any other place that has a flash video, you should be able to hear it now. Sorry about the compile 101 jargon, I just want to make sure any Ubuntu newbie can do this and maybe learn something in the process. One more thing to mention, the link I supplied is from the pulseaudio.org website. It's very hard navigating to where this link is on their website, so I made it easier.


I get this really long thing when I try that.


```
gcc -fPIC -shared -O2 -Wall -Werror  -lpthread -DLIBDIR=/usr/lib \
        -DALSA_INTERNAL  -DPULSEAUDIO -DLIBPULSEPATH='"/usr/lib/libpulse-simple.so.0"' -DESD -DLIBESDPATH='"/usr/lib/libesd.so.0"' \
        -DOSS -DOPENSSL -lssl  \
        flashsupport.c -o libflashsupport.so
flashsupport.c:195:20: error: memory.h: No such file or directory
flashsupport.c:196:19: error: stdio.h: No such file or directory
flashsupport.c:197:19: error: dlfcn.h: No such file or directory
flashsupport.c:200:25: error: openssl/ssl.h: No such file or directory
flashsupport.c:216:20: error: unistd.h: No such file or directory
flashsupport.c:217:21: error: pthread.h: No such file or directory
flashsupport.c:218:29: error: linux/soundcard.h: No such file or directory
flashsupport.c:219:23: error: sys/ioctl.h: No such file or directory
flashsupport.c:220:19: error: fcntl.h: No such file or directory
flashsupport.c:225:17: error: esd.h: No such file or directory
flashsupport.c:227:20: error: signal.h: No such file or directory
flashsupport.c:232:26: error: pulse/simple.h: No such file or directory
flashsupport.c:233:25: error: pulse/error.h: No such file or directory
flashsupport.c:248:29: error: stdlib.h: No such file or directory
flashsupport.c:249:30: error: sys/types.h: No such file or directory
flashsupport.c:250:29: error: sys/stat.h: No such file or directory
flashsupport.c:290: error: expected ‘)’ before ‘format’
flashsupport.c:295: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
flashsupport.c:300: error: expected ‘)’ before ‘*’ token
flashsupport.c:302: error: expected ‘)’ before ‘*’ token
flashsupport.c:304: error: expected ‘)’ before ‘*’ token
flashsupport.c:306: error: expected ‘)’ before ‘*’ token
flashsupport.c:308: error: expected declaration specifiers or ‘...’ before ‘*’ token
flashsupport.c:308: error: expected ‘)’ before ‘*’ token
flashsupport.c:310: error: expected ‘)’ before ‘*’ token
flashsupport.c: In function ‘FPX_SoundOutput_Detect’:
flashsupport.c:323: error: storage size of ‘buf’ isn’t known
cc1: warnings being treated as errors
flashsupport.c:331: warning: implicit declaration of function ‘getenv’
flashsupport.c:331: warning: assignment makes pointer from integer without a cast
flashsupport.c:331: error: ‘NULL’ undeclared (first use in this function)
flashsupport.c:331: error: (Each undeclared identifier is reported only once
flashsupport.c:331: error: for each function it appears in.)
flashsupport.c:334: warning: assignment makes pointer from integer without a cast
flashsupport.c:339: warning: implicit declaration of function ‘fprintf’
flashsupport.c:339: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:339: error: ‘stderr’ undeclared (first use in this function)
flashsupport.c:346: warning: assignment makes pointer from integer without a cast
flashsupport.c:347: warning: implicit declaration of function ‘strcpy’
flashsupport.c:347: warning: incompatible implicit declaration of built-in function ‘strcpy’
flashsupport.c:348: warning: implicit declaration of function ‘strcat’
flashsupport.c:348: warning: incompatible implicit declaration of built-in function ‘strcat’
flashsupport.c:349: warning: implicit declaration of function ‘stat’
flashsupport.c:350: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:355: warning: incompatible implicit declaration of built-in function ‘strcpy’
flashsupport.c:357: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:361: warning: assignment makes pointer from integer without a cast
flashsupport.c:362: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:366: warning: assignment makes pointer from integer without a cast
flashsupport.c:367: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:374: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:378: warning: assignment makes pointer from integer without a cast
flashsupport.c:379: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:387: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:394: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:399: warning: assignment makes pointer from integer without a cast
flashsupport.c:401: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:408: warning: assignment makes pointer from integer without a cast
flashsupport.c:410: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:417: warning: assignment makes pointer from integer without a cast
flashsupport.c:419: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:426: warning: assignment makes pointer from integer without a cast
flashsupport.c:428: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:437: error: ‘FPX_pa_simple_new’ undeclared (first use in this function)
flashsupport.c:438: warning: implicit declaration of function ‘dlopen’
flashsupport.c:438: error: ‘RTLD_LAZY’ undeclared (first use in this function)
flashsupport.c:438: warning: assignment makes pointer from integer without a cast
flashsupport.c:440: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:440: warning: implicit declaration of function ‘dlerror’
flashsupport.c:440: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
flashsupport.c:443: warning: implicit declaration of function ‘dlsym’
flashsupport.c:444: warning: assignment makes pointer from integer without a cast
flashsupport.c:445: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:448: error: ‘FPX_pa_simple_write’ undeclared (first use in this function)
flashsupport.c:449: warning: assignment makes pointer from integer without a cast
flashsupport.c:450: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:453: error: ‘FPX_pa_simple_drain’ undeclared (first use in this function)
flashsupport.c:454: warning: assignment makes pointer from integer without a cast
flashsupport.c:455: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:458: error: ‘FPX_pa_simple_free’ undeclared (first use in this function)
flashsupport.c:459: warning: assignment makes pointer from integer without a cast
flashsupport.c:460: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:463: error: ‘FPX_pa_simple_get_latency’ undeclared (first use in this function)
flashsupport.c:464: warning: assignment makes pointer from integer without a cast
flashsupport.c:465: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:468: warning: assignment makes pointer from integer without a cast
flashsupport.c:469: warning: assignment makes pointer from integer without a cast
flashsupport.c:470: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:476: error: ‘FPX_esd_play_stream_fallback’ undeclared (first use in this function)
flashsupport.c:477: warning: assignment makes pointer from integer without a cast
flashsupport.c:479: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:479: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
flashsupport.c:483: warning: assignment makes pointer from integer without a cast
flashsupport.c:484: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:323: warning: unused variable ‘buf’
flashsupport.c: In function ‘FPX_SoundOutput_Open’:
flashsupport.c:497: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:497: error: ‘stderr’ undeclared (first use in this function)
flashsupport.c: In function ‘FPX_Init’:
flashsupport.c:642: warning: implicit declaration of function ‘memset’
flashsupport.c:642: warning: incompatible implicit declaration of built-in function ‘memset’
flashsupport.c:669: warning: implicit declaration of function ‘SSL_library_init’
flashsupport.c: At top level:
flashsupport.c:692: error: expected specifier-qualifier-list before ‘SSL’
flashsupport.c: In function ‘FPX_SSLSocket_Create’:
flashsupport.c:700: warning: incompatible implicit declaration of built-in function ‘memset’
flashsupport.c:701: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:701: error: ‘stderr’ undeclared (first use in this function)
flashsupport.c:702: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c:702: warning: implicit declaration of function ‘SSL_CTX_new’
flashsupport.c:702: warning: implicit declaration of function ‘TLSv1_client_method’
flashsupport.c:704: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:704: warning: implicit declaration of function ‘SSL_new’
flashsupport.c:704: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c:706: warning: implicit declaration of function ‘SSL_set_fd’
flashsupport.c:706: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:710: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:711: warning: implicit declaration of function ‘SSL_shutdown’
flashsupport.c:711: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:714: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c:715: warning: implicit declaration of function ‘SSL_CTX_free’
flashsupport.c:715: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c: In function ‘FPX_SSLSocket_Destroy’:
flashsupport.c:729: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:730: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:733: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c:734: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c: In function ‘FPX_SSLSocket_Connect’:
flashsupport.c:750: warning: implicit declaration of function ‘SSL_connect’
flashsupport.c:750: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c: In function ‘FPX_SSLSocket_Receive’:
flashsupport.c:762: warning: implicit declaration of function ‘SSL_read’
flashsupport.c:762: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c: In function ‘FPX_SSLSocket_Send’:
flashsupport.c:774: warning: implicit declaration of function ‘SSL_write’
flashsupport.c:774: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c: At top level:
flashsupport.c:1113: error: expected specifier-qualifier-list before ‘pthread_t’
flashsupport.c: In function ‘oss_thread’:
flashsupport.c:1127: warning: implicit declaration of function ‘write’
flashsupport.c:1131: error: ‘struct OSS_SoundOutput_Instance’ has no member named ‘signal’
flashsupport.c:1132: warning: implicit declaration of function ‘pthread_exit’
flashsupport.c:1135: warning: implicit declaration of function ‘usleep’
flashsupport.c: In function ‘OSS_FPX_SoundOutput_Open’:
flashsupport.c:1145: error: ‘AFMT_S16_LE’ undeclared (first use in this function)
flashsupport.c:1153: warning: incompatible implicit declaration of built-in function ‘memset’
flashsupport.c:1155: warning: implicit declaration of function ‘open’
flashsupport.c:1155: error: ‘O_WRONLY’ undeclared (first use in this function)
flashsupport.c:1157: warning: implicit declaration of function ‘ioctl’
flashsupport.c:1157: error: ‘SNDCTL_DSP_SETFMT’ undeclared (first use in this function)
flashsupport.c:1159: error: ‘SNDCTL_DSP_STEREO’ undeclared (first use in this function)
flashsupport.c:1161: error: ‘SNDCTL_DSP_SPEED’ undeclared (first use in this function)
flashsupport.c:1163: warning: implicit declaration of function ‘pthread_create’
flashsupport.c:1163: error: ‘struct OSS_SoundOutput_Instance’ has no member named ‘thread’
flashsupport.c: In function ‘OSS_FPX_SoundOutput_Close’:
flashsupport.c:1180: error: ‘struct OSS_SoundOutput_Instance’ has no member named ‘signal’
flashsupport.c:1183: error: ‘SNDCTL_DSP_RESET’ undeclared (first use in this function)
flashsupport.c:1186: error: ‘struct OSS_SoundOutput_Instance’ has no member named ‘thread’
flashsupport.c:1187: warning: implicit declaration of function ‘pthread_join’
flashsupport.c:1187: error: ‘struct OSS_SoundOutput_Instance’ has no member named ‘thread’
flashsupport.c:1191: warning: implicit declaration of function ‘close’
flashsupport.c: In function ‘OSS_FPX_SoundOutput_Latency’:
flashsupport.c:1206: error: ‘SNDCTL_DSP_GETODELAY’ undeclared (first use in this function)
flashsupport.c: At top level:
flashsupport.c:1218: error: expected specifier-qualifier-list before ‘pthread_t’
flashsupport.c: In function ‘esd_thread’:
flashsupport.c:1236: error: ‘struct ESD_SoundOutput_Instance’ has no member named ‘signal’
flashsupport.c: In function ‘ESD_FPX_SoundOutput_Open’:
flashsupport.c:1251: error: ‘ESD_DEFAULT_RATE’ undeclared (first use in this function)
flashsupport.c:1253: error: ‘ESD_BITS16’ undeclared (first use in this function)
flashsupport.c:1253: error: ‘ESD_STEREO’ undeclared (first use in this function)
flashsupport.c:1254: error: ‘ESD_STREAM’ undeclared (first use in this function)
flashsupport.c:1254: error: ‘ESD_PLAY’ undeclared (first use in this function)
flashsupport.c:1255: error: ‘esd_format_t’ undeclared (first use in this function)
flashsupport.c:1255: error: expected ‘;’ before ‘format’
flashsupport.c:1257: error: ‘NULL’ undeclared (first use in this function)
flashsupport.c:1263: error: ‘format’ undeclared (first use in this function)
flashsupport.c:1266: warning: incompatible implicit declaration of built-in function ‘memset’
flashsupport.c:1269: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:1269: error: ‘stderr’ undeclared (first use in this function)
flashsupport.c:1271: warning: implicit declaration of function ‘FPX_esd_play_stream_fallback’
flashsupport.c:1273: error: ‘struct ESD_SoundOutput_Instance’ has no member named ‘thread’
flashsupport.c: In function ‘ESD_FPX_SoundOutput_Close’:
flashsupport.c:1290: error: ‘struct ESD_SoundOutput_Instance’ has no member named ‘signal’
flashsupport.c:1292: error: ‘struct ESD_SoundOutput_Instance’ has no member named ‘thread’
flashsupport.c:1293: error: ‘struct ESD_SoundOutput_Instance’ has no member named ‘thread’
flashsupport.c: At top level:
flashsupport.c:1323: error: expected specifier-qualifier-list before ‘pa_simple’
flashsupport.c: In function ‘pa_thread’:
flashsupport.c:1332: error: ‘size_t’ undeclared (first use in this function)
flashsupport.c:1332: error: expected ‘;’ before ‘len’
flashsupport.c:1336: error: ‘len’ undeclared (first use in this function)
flashsupport.c:1337: warning: implicit declaration of function ‘FPX_pa_simple_write’
flashsupport.c:1337: error: ‘struct PULSE_SoundOutput_Instance’ has no member named ‘pa_sock’
flashsupport.c:1338: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:1338: error: ‘stderr’ undeclared (first use in this function)
flashsupport.c:1341: error: ‘struct PULSE_SoundOutput_Instance’ has no member named ‘signal’
flashsupport.c: In function ‘PULSEAUDIO_FPX_SoundOutput_Open’:
flashsupport.c:1353: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:1353: error: ‘stderr’ undeclared (first use in this function)
flashsupport.c:1356: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ss’
flashsupport.c:1356: error: ‘ss’ undeclared (first use in this function)
flashsupport.c:1356: error: expected expression before ‘{’ token
flashsupport.c:1366: warning: incompatible implicit declaration of built-in function ‘memset’
flashsupport.c:1368: error: ‘struct PULSE_SoundOutput_Instance’ has no member named ‘pa_sock’
flashsupport.c:1368: warning: implicit declaration of function ‘FPX_pa_simple_new’
flashsupport.c:1368: error: ‘NULL’ undeclared (first use in this function)
flashsupport.c:1368: error: ‘PA_STREAM_PLAYBACK’ undeclared (first use in this function)
flashsupport.c:1371: error: ‘struct PULSE_SoundOutput_Instance’ has no member named ‘thread’
flashsupport.c: In function ‘PULSEAUDIO_FPX_SoundOutput_Close’:
flashsupport.c:1390: error: ‘struct PULSE_SoundOutput_Instance’ has no member named ‘signal’
flashsupport.c:1392: error: ‘struct PULSE_SoundOutput_Instance’ has no member named ‘thread’
flashsupport.c:1393: error: ‘struct PULSE_SoundOutput_Instance’ has no member named ‘thread’
flashsupport.c:1396: error: ‘struct PULSE_SoundOutput_Instance’ has no member named ‘pa_sock’
flashsupport.c:1397: warning: implicit declaration of function ‘FPX_pa_simple_drain’
flashsupport.c:1397: error: ‘struct PULSE_SoundOutput_Instance’ has no member named ‘pa_sock’
flashsupport.c:1398: warning: implicit declaration of function ‘FPX_pa_simple_free’
flashsupport.c:1398: error: ‘struct PULSE_SoundOutput_Instance’ has no member named ‘pa_sock’
flashsupport.c: In function ‘PULSEAUDIO_FPX_SoundOutput_Latency’:
flashsupport.c:1411: error: ‘pa_usec_t’ undeclared (first use in this function)
flashsupport.c:1411: error: expected ‘;’ before ‘latencytime’
flashsupport.c:1416: error: ‘struct PULSE_SoundOutput_Instance’ has no member named ‘pa_sock’
flashsupport.c:1417: error: ‘latencytime’ undeclared (first use in this function)
flashsupport.c:1417: warning: implicit declaration of function ‘FPX_pa_simple_get_latency’
flashsupport.c:1417: error: ‘struct PULSE_SoundOutput_Instance’ has no member named ‘pa_sock’
flashsupport.c:1419: warning: incompatible implicit declaration of built-in function ‘fprintf’
flashsupport.c:1419: error: ‘stderr’ undeclared (first use in this function)
make: *** [libflashsupport.so] Error 1

```

---

### Post by eldragon on 2008-03-04
same problem happened here.

you need to check your permissions in your home dir.

i did: sudo chown -R eldragon:eldragon ~/.macromedia

this restored sound for me.

i also stole ownership doing the same to ~/.adobe

but im not sure if its needed or not. anyway, its your home, you should own your stuff there ;)

i think the user that gets all this problems is the one that installs the flash player in the first place.
future users dont have this problem

---

### Post by bouss on 2008-03-05
> **ubukool said:**
> Hi everyone,

You might want to try this, it worked for me!  Nice and easy:

[http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/)

Good luck :)

This worked for me too. Thanx a lot mate.

---

### Post by SendDerek on 2008-04-14
> **ubukool said:**
> Hi everyone,

You might want to try this, it worked for me!  Nice and easy:

[http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/)

Good luck :)

I wanted to drop by and let people know that the link referred to above has been moved to this address:

[http://www.derekhildreth.com/blog/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://www.derekhildreth.com/blog/how-to-fix-the-no-sound-issue-in-firefox-flash/)

The old link will still work, but it will no longer be updated and I will will not follow up on any new comments either.  Please refer to the new address.

Thanks,

-Derek

---

### Post by otakudc on 2008-04-17
> **Temüjin said:**
> For anyone on AMD64 trying to compile libflashsupport for use with the 32-bit Flash plugin, you'll need to comment out the #define OPENSSL line in the flashsupport.c file.

Get gcc 4.1 or better and its corresponding multilib package and compile with the -m32 flag. Example:
```
sudo apt-get install gcc-4.1 gcc4.1-base gcc-4.1-multilib build-essential
cc -shared -O2 -Wall -Werror -m32 -fPIC flashsupport.c -o libflashsupport.so
```

Then put your new libflashsupport.so file in /usr/lib and put symbolic links in /usr/lib32, /usr/lib/firefox/plugins, and /usr/mozilla/plugins

Thanks for addressing the AMD64 issue, I think that's why none of the other solutions have worked for me. However, I'm new to Ubuntu (and Linux in general) and don't quite know what you mean by putting symbolic links.

Also, when I ran that code I got this:```


andres@andres-desktop:~$ cc -shared -O2 -Wall -Werror -m32 -fPIC flashsupport.c -o libflashsupport.so
cc: flashsupport.c: No such file or directory
cc: no input files
```

I'm guessing I'm in the wrong folder but have no idea where the right one would be. Any help would be appreciated. Thanks!

---

### Post by thevoidreturns on 2008-04-19
This is a response to Eldragon suggestion, it worked perfect for me. Although, before coming to this suggestion I have tried the combination of other solutions including the pulseaudio and libflashsupport ways. It did turn out to be a permission issue as I created a new user first and flash worked in the new account, but not in the original.

I did have to alter both the macromedia and adobe files.

Thanks for the solution :popcorn:

---

### Post by war59312 on 2008-05-20
Still lame as hell that you cant listen to two audio sources at once. :(

---

### Post by no-use on 2008-06-11
I just solved a smilar issue for me, I've searched like crazy for this so here I am sharing it.

I believe my problem was due to my 2 sound cards.
Setting applications to use alsa as the audio output made sound work for me everywhere but in firefox.

Alsa's asoundconf just fixed it however.

First I displayed my soundcards using:

```
asoundconf list

Names of available sound cards:
au8830
V8237

```

Then I selected my default one:

```
asoundconf set-default-card au8830
```
[INDENT][SIZE="1"]Note: you don't need to 'sudo' this command[/SIZE][/INDENT]


This however is probably only a fix for people having this problem with a similar setup as I do.

---

### Post by snook on 2008-06-23
None of these ideas worked for me, but I found one that does. First, go to Synaptic and download all of the Pulse Audio packages

Thanks!  doing the simplest thing first, i dl'ed all the packages, and it works now.

---

