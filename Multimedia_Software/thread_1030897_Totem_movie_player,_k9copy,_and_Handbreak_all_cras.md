---
title: "Totem movie player, k9copy, and Handbreak all crash"
date: 2009-01-04
forum: Multimedia Software
---

### Post by craftypants on 2009-01-04
I think something's fishy video-wise on my machine, but I have no idea what to do. When I put a DVD in the drive, Totem movie player launches, then crashes (could not read from source). If I launch k9copy then put in a disc, k9copy will crash (SIGSEGV). Handbreak won't launch at all. What's going on?

---

### Post by rushikesh988 on 2009-01-04
may be ur DVD is damaged 

Or  

u don't have sutaible codecs of DVD movies




try putting another DVD  _OR_ 


USING ANY OTHER PLAYER

---

### Post by craftypants on 2009-01-04
I tried that. Yes, I can watch DVDs with any other player. I'm just wonder if something is missing that would cause issues with all three of these things. I have the correct codecs and have tried many different discs.

---

### Post by wolfen69 on 2009-01-04
it sounds like your computer just does not like whatever ubuntu version you are using. if you are using intrepid ibex, maybe try hardy heron? sometimes that's all it takes is a different version.

---

### Post by coffeecat on 2009-01-06
> **craftypants said:**
> If I launch k9copy then put in a disc, k9copy will crash (SIGSEGV).

Which version of Ubuntu are you using? I cannot get k9copy to behave in Intrepid, but in Hardy it works just fine on the same machine. The (earlier) version of k9copy in Hardy runs with the KDE3 libraries, but the Intrepid version is a KDE4 one, so I wonder if there is a problem with the kde4 libraries in Gnome. That doesn't explain your problems with Totem though.

Yes, I'm getting SIGSEGV crash reports as well. That is if k9copy survives its initial greying out sulk mode. And just before I posted, this popped up on my desktop:

> A Fatal Error Occurred
 The application k9copy (k9copy) crashed and caused the signal 6 (SIGABRT).Except that I wasn't running k9copy - hadn't been for 5 minutes.


I wonder if anyone has been able to get k9copy to work in Intrepid. I was going to start a thread about this, but then I found this one.

---

### Post by coffeecat on 2009-01-06
I happen to have Intrepid installed on a second machine, so I thought I'd try k9copy on that as well. After about ten minutes of copying, guess what?

> A Fatal Error Occurred
 The application k9copy (k9copy) crashed and caused the signal 11 (SIGSEGV).
Now where have I seen that before? :roll:


Has **anyone** managed to get this app to work in Intrepid/gnome? Was it QA'd before being released onto the mirrors?

---

### Post by craftypants on 2009-01-06
> **coffeecat said:**
> Which version of Ubuntu are you using? 

I'm using Hardy. For some reason I thought it was Intrepid when I downloaded Handbrake (which explains why Handbrake doesn't work for me, I had the wrong version). 

Are there any tips/tricks/things I should download to get k9copy to work in Hardy? I checked their site and I have all the necessary prereq's.

---

### Post by johnmarkbuchanan on 2009-01-07
I'm also having problems with Totem, and every other player I try. I was never prompted to DL additional codecs, upon trying to play a dvd I recieved the error "Could not open location; you might not have permission to open the file." 
If it is indeed the codecs I am missing, how do I go about installing them?

---

### Post by amast on 2009-03-28
> **coffeecat said:**
> I happen to have Intrepid installed on a second machine, so I thought I'd try k9copy on that as well. After about ten minutes of copying, guess what?  Has **anyone** managed to get this app to work in Intrepid/gnome? Was it QA'd before being released onto the mirrors?
As of March 28, 2009 K9copy still crashes on Intrepid Ibex.  It's too bad because it looks like a cool app and I was excited to use it.  Every post regarding this error just dies out.  No significant report of a fix that I could find.  :(

---

### Post by ajoliveira on 2009-04-06
Hi

Got two laptops with Xubuntu 32 bits, kde 3.5.10 installed underneath. k9copy and totem are installed on both. One has  2.6.27-14-server, the other regular  2.6.27-14. Video cards are different. server kernel has a sis, the other an nvidia. k9copy and totem work on the non-server and crash on the server kernel.

ASSERT failure in QList<T>::at: "index out of range", file /usr/include/qt4/QtCore/qlist.h, line 393
KCrash: Application 'k9copy' crashing...
sock_file=/home/ajoliveira/.kde/socket-melro/kdeinit4__0
Warning: connect() failed: : No such file or directory
KCrash cannot reach kdeinit, launching directly.

Application: k9copy (k9copy), signal SIGABRT

Thread 1 (Thread 0xb5d178e0 (LWP 7176)):
[KCrash Handler]
#5  0xb804a424 in __kernel_vsyscall ()
#6  0xb64428a0 in raise () from /lib/tls/i686/cmov/libc.so.6
#7  0xb6444268 in abort () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7249795 in qt_message_output () from /usr/lib/libQtCore.so.4
#9  0xb7249872 in qFatal () from /usr/lib/libQtCore.so.4
#10 0xb72498cc in qt_assert_x () from /usr/lib/libQtCore.so.4
#11 0x080b06be in _start () 

This seems to be a library fault, and recently I had some kind of xserver-xorg-video-intel upgrade recently, and I could not understand why...

******************************

this was the upgrade, taken from /var/log/apt/term.log

Log started: 2009-04-01  10:29:40
(Reading database ... 178615 files and directories currently installed.)

Preparing to replace libldap-2.4-2 2.4.11-0ubuntu6.1 (using .../libldap-2.4-2_2.4.11-0ubuntu6.2_i386.deb) ...

Unpacking replacement libldap-2.4-2 ...

Preparing to replace foo2zjs 20080810-0ubuntu4 (using .../foo2zjs_20080810-0ubuntu4.1_i386.deb) ...

Unpacking replacement foo2zjs ...

Preparing to replace xserver-xorg-video-intel 2:2.4.1-1ubuntu10.3 (using .../xserver-xorg-video-intel_2%3a2.4.1-1ubuntu10.4_i386.deb) ...

Unpacking replacement xserver-xorg-video-intel ...

Processing triggers for man-db ...

Setting up libldap-2.4-2 (2.4.11-0ubuntu6.2) ...

as soon as i got a bit of time i will try to roll back and compare the versions on the 2 laptops...

cheers

Antonio

---

### Post by mysoogal on 2009-04-06
maybe this will help

```
sudo apt-get update
sudo apt-get dist-upgrade
```


you need the gstreamer plug-ins also the mpeg2/4 decoders installed

synaptic package manager look for gstreamer and install anything that says gstreamer 

I'm on Acer 5315 my ubuntu is fully updated and everything working good with the totem Movie player, I even removed VLC :lolflag:

---

### Post by ajoliveira on 2009-04-08
Hello

In what k9copy was concerned I posted the fix I used [here]("http://ajoliveira.com/ajoliveira/uk/software/k9copy.php")

totem only has problems if I run it as root

take care

Antonio

---

### Post by Scubdup on 2009-06-09
Just to add - I've got the exact same problem. Bit rubbish to be honest. Firefox keeps greying out for me too. :(

---

### Post by Scubdup on 2009-06-09
...And I think I've found the solution. Install the Medibuntu stuff [here]("https://help.ubuntu.com/community/Medibuntu"). Seems to have worked for me.

---

### Post by ubu2008 on 2009-06-14
2009/06/14
Ubuntu 9.04
Unfortunately I do not have a solution, but I can provide additional data.

Experiment 1:
Start totem as line cmd, get the following warning. The totem sits there waiting, it does not crash.

>totem 
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead 
  import sha 

//Now, drop a movie onto totem, get the following:

The program 'totem' received an X Window System error. 
This probably reflects a bug in the program. 
The error was 'BadAlloc (insufficient resources for operation)'. 
  (Details: serial 91 error_code 11 request_code 132 minor_code 19) 
  (Note to programmers: normally, X errors are reported asynchronously; 
   that is, you will receive the error a while after causing it. 
   To debug your program, run it with the --sync command line 
   option to change this behavior. You can then get a meaningful 
   backtrace from your debugger if you break on the gdk_x_error() function.) 
//and crash



Experiment 2:

Start gxine from line, it will open and not crash.

>gxine 

//It reports this message.
warning: configuration item media.audio_cd.cddb_cachedir points to a non-existent location /home/thisuser/.xine/cddbcache 
warning: configuration item media.capture.save_dir points to a non-existent location 
warning: configuration item media.dvb.channels_conf points to a non-existent location /home/thisuser/.xine/channels.conf 
warning: configuration item media.vcd.device points to a non-existent location 
warning: configuration item media.video4linux.radio_device points to a non-existent location /dev/radio0 
warning: configuration item media.video4linux.video_device points to a non-existent location /dev/video0 
warning: configuration item media.wintv_pvr.device points to a non-existent location /dev/video0 
warning: configuration item decoder.external.real_codecs_path points to a non-existent location 
warning: configuration item decoder.external.win32_codecs_path points to a non-existent location /usr/lib/codecs 
warning: configuration item subtitles.separate.font_freetype points to a non-existent location 
lirc: cannot initialise - disabling remote control 
lirc: maybe lircd isn't running or you can't connect to the socket? 



//Drop movie into gxine, it does not crash, but no video shown, but yes audio heard.


Experiment 3:

Start gxine from line.
>gxine 
warning: configuration item media.audio_cd.cddb_cachedir points to a non-existent location /home/thisuser/.xine/cddbcache 
warning: configuration item media.capture.save_dir points to a non-existent location 
warning: configuration item media.dvb.channels_conf points to a non-existent location /home/thisuser/.xine/channels.conf 
warning: configuration item media.vcd.device points to a non-existent location 
warning: configuration item media.video4linux.radio_device points to a non-existent location /dev/radio0 
warning: configuration item media.video4linux.video_device points to a non-existent location /dev/video0 
warning: configuration item media.wintv_pvr.device points to a non-existent location /dev/video0 
warning: configuration item decoder.external.real_codecs_path points to a non-existent location 
warning: configuration item decoder.external.win32_codecs_path points to a non-existent location /usr/lib/codecs 
warning: configuration item subtitles.separate.font_freetype points to a non-existent location 
lirc: cannot initialise - disabling remote control 
lirc: maybe lircd isn't running or you can't connect to the socket? 
//Do not do anything else with gxine, let it run.

//From another window, start totem from line.
>totem


//get this message.
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead 
  import sha 

//Drop movie into totem.
//The movie plays fine both audio and video.
//In case you care the file type is .wmv

Regards.

---

