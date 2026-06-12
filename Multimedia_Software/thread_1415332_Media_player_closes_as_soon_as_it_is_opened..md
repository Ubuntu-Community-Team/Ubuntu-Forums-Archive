---
title: "Media player closes as soon as it is opened."
date: 2010-02-24
forum: Multimedia Software
---

### Post by Tayashlor on 2010-02-24
OKay... here's my problem. 

Im currently running Unbuntu 9.04. Yesterday my Mplayer has suddenly quit working properly. So, I downloaded VLC. Both programs, when a video file is opened, the media player will open for a moment, and then close again. If the program is opened first, and then the movie file opened, it still happens. I've read other posts and they all said to run "totem" in terminal. This is what I recieved:

steve@steve-laptop:~$ totem

(totem:7419): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
    'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 586 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Can someone please tell me what I can do to fix this . 

Thanks in advance.

---

### Post by Ozymandias_117 on 2010-02-24
I had the exact same problem... What I did was "sudo apt-get purge ubuntu-restricted-extras" "sudo apt-get purge vlc" "sudo apt-get update" "sudo apt-get autoremove" "sudo apt-get dist-upgrade" (I doubt this is important, but I did it, so I'm posting it) then I rebooted. then "sudo apt-get install ubuntu-restricted-extras" "sudo apt-get install vlc"

---

### Post by andrew.46 on 2010-02-24
Hi Tayashlor,

> **Tayashlor said:**
> Both programs, when a video file is opened, the media player will open for a moment, and then close again. 

This can be a sign that the default video out selected by MPlayer and vlc is incompatible with your current setup. You can test this idea by altering the video out device utilised by vlc for example:

Tools --> Preferences --> Video --> Output

and experimenting a little with the outputs available to you. A safe choice is x11...

All the best,

Andrew

---

### Post by Tayashlor on 2010-02-24
> **andrew.46 said:**
> Hi Tayashlor,



This can be a sign that the default video out selected by MPlayer and vlc is incompatible with your current setup. You can test this idea by altering the video out device utilised by vlc for example:

Tools --> Preferences --> Video --> Output

and experimenting a little with the outputs available to you. A safe choice is x11...

All the best,

Andrew

I also tried this, because i saw it in another post, and the only option it gives me is default...

---

### Post by Tayashlor on 2010-02-24
okay... the first two.... 

steve@steve-laptop:~$ sudo purge ubuntu-restricted-extras
sudo: purge: command not found

steve@steve-laptop:~$ sudo purge vlc
sudo: purge: command not found


the update ran.... but said there were duplicate problems... 

Im not sure if im doing anything wrong....

---

### Post by Ozymandias_117 on 2010-02-24
Sorry, no, I just was half asleep :D What I meant was "sudo apt-get purge ubuntu-restricted-extras" and "sudo apt-get purge vlc"

---

### Post by andrew.46 on 2010-02-24
Hi Tayashlor,

> **Tayashlor said:**
> I also tried this, because i saw it in another post, and the only option it gives me is default...

That is a little odd. I attach a screenshot to show what *should* be there, your options will be a little different because I am running vlc-git...

Andrew

---

### Post by Tayashlor on 2010-02-24
> **andrew.46 said:**
> Hi Tayashlor,



That is a little odd. I attach a screenshot to show what *should* be there, your options will be a little different because I am running vlc-git...

Andrew

I went back to the prefrences again, and when i click its an empty list.

---

### Post by Tayashlor on 2010-02-24
so i just ran all the commands from the first post. it uninstalled and reinstalled vlc. the only thing that has changed is now my vlc icon is a weird gray box with white outline. when i tried to play a .avi file, it sill opened and then closed 5 seconds later.

---

### Post by Ozymandias_117 on 2010-02-24
I have the same icon problem, but it had fixed my playback =( Sorry.

---

### Post by Tayashlor on 2010-02-24
> **Ozymandias_117 said:**
> I have the same icon problem, but it had fixed my playback =( Sorry.

i just tried it again, and the first time it turned off, then i clicked it again, and it loaded, but there was no video

upon closing and trying to reopen it continues to turn off

---

### Post by Tayashlor on 2010-02-25
still having problems. any help?

---

### Post by Tayashlor on 2010-02-25
okay, so i just realized that in the VLC properties, it was not an empty drop down box, instead i just couldnt see what it was saying (i dont know why, drop downs work in any other window) 
i changed the output to x11 and still having the same problem. 

can anyone help? please i'll try anything at this point. 

i even tried to download some other video players and they dont work with .avi files.

---

