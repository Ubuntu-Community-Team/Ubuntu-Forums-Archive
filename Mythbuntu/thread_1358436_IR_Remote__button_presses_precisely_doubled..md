---
title: "IR Remote  button presses precisely doubled."
date: 2009-12-18
forum: Mythbuntu
---

### Post by LarryJ2 on 2009-12-18
I just completed installation of  Mythbuntu .22 9.10 64 bit. Pressing a button on my previously working remote control issues exactly, precisely two (double) the key presses into the frontend.  For example, here is the output of the arrow  button press sequence right, left, right ,left   

> lj@mythtv:~$ ircat mythtv
Right
Right
Left
Left
Right
Right
Left
Left


This oddity does not depend on how quickly you press and release the remote keys.  So it's not a matter of  repeat or delay.  Something more fundamental came along with the installation of  .22 that seems to take a single ir remote button press and output exactly two keypresses into Mythbuntu.

My ~/.lirc/mythtv is the same as my previous install of  .21 on 8.04 which was working just fine.   The ir remote is also the same as is the Hauppauge 1600 to which it is attached.

Previously I installed the 32 bit version of Mythbuntu .22 on 9.10.  It had the same problem so I decided to try the 64 bit version.  Both have this oddity.

I'm out of ideas.  Suggestions?

Larry

---

### Post by azmyth on 2009-12-18
Try adding a repeat command to your .lircrc for the buttons that are causing you problems something like repeat = 2.

[http://www.lirc.org/html/configure.html](http://www.lirc.org/html/configure.html)

---

### Post by LarryJ2 on 2009-12-18
Thanks but "repeat =" doesn't work as far as I can tell.

What does help (I think) is  to  cd to the mythbuntu 9.10 / myth .22  directory
/usr/share/lirc/remotes/mceusb

In that directory is a file "lircd.conf.mceusb"

In the first section dedicated to  "mceusb",  I
put this line after the "gap" line:

> min_repeat      0 

Here's  part of that file after the change was made:

> begin remote

  name        mceusb
  bits                 16
  flags  RC6|CONST_LENGTH
  eps                  30
  aeps                100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits        21
  pre_data        0x37FF0
  gap              105000
**  min_repeat      0** 
  toggle_bit           22
  rc6_mask    0x100000000

This came from a brief post by Jerald Wilson on the MythUsers mailing list. (Google min_repeat in the Gossamer Threads repeat of the MythUsers Mailing List)  I didn't understand it but it seems to work. Maybe someone else can confirm?

---

### Post by SiHa on 2009-12-19
Well, I didn't think I had this problem, as I only get the occasional repeat, thought it was something else. But I thought I'd try this solution, and, on checking with irw beforehand, every button press is repeated exactly as you have. God only knows why they don't all get through to Myth.

Anyway, unfortunately, adding this line to my lircd.conf did't work.

---

### Post by SiHa on 2009-12-19
A bit more digging, and I find that the problem I have is only when using a 'One For All' universal remote, where I have had to 'learn' all the buttons. Each one sends a press and a repeat (ie, the repeat index inreases0,1). I've verified this by covering the sender immediately after pressing the button, and only one press gets through. 
I have the repeat = 0 in my ~/.lirc/mythtv and that filters out all of these. Where I get the skips in Myth is where it sends two separate presses (ie, repeat index = 0,0) these are both passed onto Myth.
So my problem, seems to be subtly different to yours.

It doesn't happen when using the original Hauppauge RC, either, so I'll have to use that until I can get the OFA people to program the remote properly.

---

### Post by LarryJ2 on 2009-12-19
SiHa

When I ran irw,  I also got sporatic keypresses displayed.  Press Left and sometimes two lefts sometimes one left would appear.  

But when I ran  ircat mythtv,  every press of the left remote button would yield exactly (no more not less than) two lefts. 

I'm not certain my fix fixed this.  I'm only humbly grateful that it worked.  I tore down a working copy myth.21 and 8.10.  Everything was working great!   Then I  installed  myth.22 on 9.10   Nothing but troubles so far.   A lesson I never seem to learn where myth is concerned.  If it works don't touch it!

Great fun playing never the less.

Larry

---

