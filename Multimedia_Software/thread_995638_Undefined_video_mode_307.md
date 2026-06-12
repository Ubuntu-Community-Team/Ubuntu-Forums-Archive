---
title: "Undefined video mode: 307"
date: 2008-11-28
forum: Multimedia Software
---

### Post by anualan on 2008-11-28
Hi,
I'm new to Ubuntu and have just switched over from Windows Vista.
On booting Ubuntu from the grub menu i get a message
"Starting Up
Undefined video mode number:307
Press <ENTER> to see video modes available, <SPACE> to continue, or wait 30 seconds: "

If I wait for 30 second the system will boot up. 

If I press <ENTER> i get a list with about 6 modes listed as below,

Mode:       COLS x ROWS
0           80x25      VGA
1           80x50      VGA
2           80x43      VGA
3           80x28      VGA
4           80x30      VGA
5           80x34      VGA
6           80x60      VGA

Enter a video mode or "scan" to scan for additional modes:"

On entering "scan" I get the same modes as listed above.

I have a NVIDIA integrated graphics card 6150 LE

Can some one please help ?

If i run glxinfo in a terminal window i get the following a long list which I am attaching as a text file.

---

### Post by tmartindub on 2009-03-07
Did you ever fix this problem?  I am now new to Ubuntu and am getting this error, after not having got it for a month.

I have no idea what it means.

tm

---

### Post by Ampersand. on 2009-03-25
+1

I added DosBox to play some old school 16 bit games and that is when this started happening.
It really isnt a problem but it would be nice to make it go away

EDIT: 
well now it has changed to Undefined video mode: 31a since i changed the colour settings in startup manager from 8bit to 24 bit.

---

### Post by craigchambers on 2009-09-10
I got the same problem as the OP after I downloaded some updates, one of which was the latest version of Grub.  I fixed the issue by following the steps at this site: [Undefined Video Mode Number]("http://http://gusantov.blogspot.com/2008/05/undefined-video-mode-number.html")
> 1. Open your menu.lst file
sudo gedit /boot/grub/menu.lst
2. Change statement that says vga=xxx (xxx is some numbers) with vga=normal
3. Reboot 

Hope this helps someone else!

/Craig

---

### Post by 741Baus on 2009-12-27
I have had this same minor problem after getting a new graphics card for Christmas I followed your direction and it worked a charm thanks for that craigchambers you :guitar:

---

