---
title: "real time kernel available in synaptic for Dapper i386!"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by damu on 2006-09-20
We can thank [this french team]("http://ubuntu.ttoine.net/doku.php?id=installer_ubuntu-musique") for bringing to us real time audio processing in  just few clicks !


**_How to_**

_Add the ubuntu-musique repositories_

  1.Open Synaptic (system/administration/synaptic)
      
  2.Go to settings/repositories
     
  3.in the new window, click on the 'add' button

  4. click on the 'custom' button

  5. copy and paste > deb [http://ubuntu.ttoine.net](http://ubuntu.ttoine.net) dapper-music main testing

  6. click 'add channel

  7. now that the the ubuntu-musique repositories have been added to synaptic, you need to click the 'reload' button on synaptic, so that the new repositeries get listed in Synaptic.
     
[U]
Install the real time kernel
[/U]
  

  1. do a search in synaptic with > musique
   
  2. mark the package 'ubuntu-musique" for installation

  3. click 'apply'


[U]
To start ubuntu-musique[/U]

You just need to choose the kernel with 'ubuntu musique' in the list  which is displayed at boot.

[U][B]
Read first[/B][/U] 

1. this new kernel only works for 'one core' processors. For AMD dual core processors, only one core will be seen by the system. It still works (no xruns), but defeats the object for heavy audio projects...stay tune: as mentionned in other posts, Ubuntu Edgy might help a bit + the ubuntu.toine.net team is working on a new version of kernel which should support smp.

2. the last version of kernel in Ubuntu-musique is the kernel 2.6.17.6-rt7. Ubuntu-musique might install by default the previous version 2.6.15.26-rt21 (which is working fine for me). So if it is the case and that you want to have the last kernel available of Ubuntu-musique, go back to synaptic and check that the last kernel is installed. If not, mark it for installation, and apply.

3. if you have a dual boot system (with Windows XP or other OS), backup you menu.lst before upgrading the kernel with syanptic...each time I go through an upgrade of kernel, my menu.lst is updated and Windows XP disappears of the list (a sign ?...;) )...it's not a big deal: 
 a) open a terminal window (accessories/terminal), and copy and paste: > sudo gedit boot/grub/menu.lst 
 b) "save as" 'my-menu.lst' in your home folder.
 c) reboot . If your list in grub is ok, and that both systems are listed, you're lucky. If not:
 d) open your menu.lst by following the procedure (a) and open 'my-menu.lst' which is in your home folder. 
 e) In 'my-menu.lst', detect the block of text which mentions the missing OS . For me, it looks like 
> title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
 f) copy this block of text and paste it in menu.lst just above the similar blocks of text. Make sure that you leave an identical space before and after the block.

 g) save menu.lst

That's it ...you're done.


Enjoy!

---

### Post by Patrice Brousseau on 2006-09-21
I tried the 2.6.17 musique kernel but to my surprise, my 2 FAT32 partitions aren't available anymore...

I will try the 2.6.15 one but if it has the same problem, I'll stick to my own realtime compiled kernel.

Thanks anyway for the information.

---

### Post by Patrice Brousseau on 2006-09-21
2.6.15 works fine...

---

### Post by HanZo on 2006-09-21
I suppose this is not going to work in edgy yet, is it?

---

### Post by Patrice Brousseau on 2006-09-21
You could try and at worst, your machine won't boot with this kernel but you could always go back to your original working kernel... (maybe it is best to make a complete image of your system however to prevent anything that could damage irremediably your Edgy OS)

I'm far from a Linux expert so I do not know if Dapper kernels could work on an Edgy install...

---

### Post by HanZo on 2006-09-22
I'll try... I'm running edgy for testing purpose only so in the worst case I'll just reinstall...
I'm just evaluating the possibility to use ubuntu for my music making needs...

---

### Post by darthvim on 2006-09-24
hi, i've trie out the kernel with rt but the x server didn't start because of 
the nvidia module which couldn't be found...

how can i get this working
i've tried to install nvidia-glx through apt-get but it wasn't found.

any suggestions ?

greetings
darthvim

---

### Post by js72 on 2006-09-26
Does your usplash work with this kernel?
Here is only blanc screen (normal?)
Everything else seems okay and good!

---

### Post by dolson on 2006-09-26
No, uspash does not work with this kernel.

This is no different from one you would get by compiling it yourself using the instructions in the Ubuntu Studio Project wiki. In fact, they used my tutorial there to create it.

---

### Post by js72 on 2006-09-27
So next quest, should i have "verbose" mode in boot cause still
black blanc screen only and x comes to alive when gdm starts.

---

### Post by dolson on 2006-09-27
You should be able to modify grub just like my wiki says.

That French team has said that this stuff is not meant for wide use, and in fact we are trying to work with them towards Mubuntu.

---

### Post by Aurora on 2006-09-28
I took the plunge and have started building my first computer. I chose AMD 64--is this kernal going to work?  Have I caused myself a lot of problems with my choice of processor?

---

### Post by dolson on 2006-09-28
As far as I know they only support i386. And hence the issue with me having any desire to promote or support the use of 3rd-party repositories.

However, they only followed my tutorial and didn't build it like a distro packager would, so if you follow the wiki page, you'll get a kernel that will work for you.

---

### Post by zettberlin on 2006-10-08
As I test edgy eft I found it unusable with the Stock-kernel it is packed with recently 200 xruns within  a minute just for moving windows around the screen - same "performance" as known from Suse 9.3 and worse.

So I desperately searched for a solution and decided to install the "testing"-kernel from ttoine AND 

It works just right away!! :D :D 

Some evil benchmarks (starting ams with 6 VCO and 12xpoly and stuff like such) still makes an end to everything but it has indeed at last the powers, dappers DESKTOP_PREEMPT-Kernel once had.

Thank you very much! 
Thus I can stay with UBUNTU without hacking Dapper for new Progs upgrade like everybody else :-)

---

### Post by falkenberg_cph on 2006-11-28
Man im having little succes tonite. Im trying to install this. But its dependent of some package, thats dependent of jamloader, which again needs python-wxgtk, so i installed both 2.6 and 2.4, but it keeps saying it isnt installed?

/Carsten

---

### Post by akselvonpaksel on 2006-11-29
It seems there is an interesting audiodistro just out. All ready for realtime and 64bit processors:

[http://64studio.com/](http://64studio.com/)

It may not have the ease of *buntu, but you cant get it all...

---

### Post by hogiewan on 2007-01-23
I tried to install the packages on edgy and I got errors in synaptic, so I tried installing just the kernel and kernel-headers packages and it installed and booted properly.   I told X to use the nv driver instead of the nvidia driver before rebooting.  The system booted fine and my FAT and NTFS partitions were available.  My gina20 card didn't load, so I'll probably need to recompile alsa again (had to compile with the stock ubuntu kernel).

I tried removing the nvidia-glx packages and reinstalling them, but it seems to want to use the package for the stock kernel and not the musique kernel, which is just a bit older.  I'm not terribly familiar with ubuntu or debian , even, as I grew up on slackware.  any help getting nvdia driver to work would be great as I need the twinview option

---

### Post by justin13 on 2007-06-04
well that repo is dead for sure =/
sigh i faild on compiling the very very latest kernel with rts/lowlatency... hopefully i can bug the ustudio guyz to take pity! had to downgrade to dapper as feisty was waaaaaaaaaaaaaay out of control on buggyness

---

