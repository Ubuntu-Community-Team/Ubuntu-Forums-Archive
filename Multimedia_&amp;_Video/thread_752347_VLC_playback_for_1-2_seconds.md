---
title: "VLC playback for 1-2 seconds"
date: 2008-04-11
forum: Multimedia &amp; Video
---

### Post by arpinology on 2008-04-11
I installed the VLC package last week; overall I liked the program when i use a windows machine and appreciate that it supports many file types/codecs.  so i felt why not have it on my linux box. 

So it works...occasionally.  It almost chooses when to playback and when not to playback, and for a variety of files.  

I should say that it does play back, but for only for a second.  The window pops up, i see a blank black screen(or occasionally a frame from the video) and i can usually hear a second or 2 of sound, then the program closes itself.  

It has worked though; I just used it two nights ago and the video playback was perfect.  It still gives me trouble on some files though. Now it wont work for the exact same files I used the other night.  

Anybody hear of this?  I read somewhere about desktop effects affecting video playback.  Just thought I'd throw it out there. 

I couldnt find anything totally relevant in this forum.  

OH also, I uninstalled totem, but i did that after all this wouldnt work; that program is just useless to me.

---

### Post by arpinology on 2008-04-11
First quick update:

installed the mplayer package and i have the same problem with that, but i received a message that said 

gnome_screensaver_control.  im going to do some research and see what that may provide.


Second quick update:

I searched the internet, found something i thought...very loosely may apply, but that i may need later.  the posting(on this forum) said to uninstall vlc, install libdevcss2 from synaptic package manager, then re-install vlc.  

i did that, and just tried it out to see if it would work..AND IT DID.  but then i went to try it again 5 minutes later, and it didnt(exact same file as what worked 5 minutes before.)  i rebooted my computer and still nothing.

very very frustrating.  not having video capabilities is very discouraging.

---

### Post by deadgobby on 2008-04-11
Did you install all restricted CODES from synaptic? Did you try to run VLC play in the terminal and see what error codes comes up?

---

### Post by arpinology on 2008-04-11
thanks for the quick reply.

what would these "restricted codes" be under in synaptics?  i searched and i could not find them.  

as for initiating it in terminal, i did do that, it loads, says 
 
vlc media player 0.8.6c Janus

eric@eric-desktop:~$ vlc
VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86
pure virtual method called
terminate called without an active exception
Aborted (core dumped)
eric@eric-desktop:~$ 

this is the output after i attempted to open a file.  

bad allocation sounds interesting.  im going to look it up.

any ideas?

---

### Post by deadgobby on 2008-04-11
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Here how to get them
Gobby
VLC never had a problem playing all formats.

---

### Post by arpinology on 2008-04-11
i received this output when attempting to load a file through totem(to see if i'd get the same or a very similar response)

eric@eric-desktop:~/movies$ totem
sh: jackd: not found
sh: jackd: not found
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 58 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
eric@eric-desktop:~/movies$ 


i did.  ha.

---

### Post by deadgobby on 2008-04-11
What Audio Program are you trying to run. It is calling for Jackd. have you tried VLC player?

---

### Post by mc4man on 2008-04-11
sounds more like a video driver, settings or video output  issue than a codec one

---

### Post by arpinology on 2008-04-12
> **mc4man said:**
> sounds more like a video driver, settings or video output  issue than a codec one

where do you think i should start with this then?

---

### Post by Trollslayer on 2008-04-13
How much RAM do you have and which video card and driver?
You need to install a driver for the card, the default VESA driver is a generic driver that does not support acceleration for video.

---

### Post by xc3RnbFO8P on 2008-04-13
> **arpinology said:**
> where do you think i should start with this then?

In Vlc: Settings> Preferences> video> Output Modules (check Advance options, bottom right) and try:  **x11**

---

### Post by rackub on 2008-04-18
RIngi - You are a Genius!! 

You have just stopped one ubuntu newbie (though with more than a few grey hairs by now) who was on the verge of returning to W******.

I have been trying to get DVDs to play for hours, trying numerous players, codecs etc and was getting the same 2 seconds and then close and BadAlloc error

I don't know what x11 is or does but it worked.

If anyone can explain this solution I would be interested to understand what the issue was and why x11 sorts it.

---

