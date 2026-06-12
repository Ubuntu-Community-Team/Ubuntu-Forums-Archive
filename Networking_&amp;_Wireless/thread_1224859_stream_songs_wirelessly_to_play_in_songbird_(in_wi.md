---
title: "stream songs wirelessly to play in songbird (in windows)"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by aaronLund on 2009-07-27
Yes.....windows.  Hey, the wife is still clinging...

The share (ext3) is a lone usb drive on my computer which is running (8.04/Hardy.....they call it that for a reason!).  It is shared and I can currently see it from her computer.  

Even connect to it.

I don't want to download the songs to her computer.  In fact, she uses Itunes (ipod owner, etc).  I'd just like to stream them to her computer.  

Is this even possible?  

I should add that I chose a separate app to do this (Songbird) as I didn't want our libraries to interact.  She doesn't enjoy Judas Priest as much as I do, apparently.

I have yet to find a VNC Server that serves a reliable Ubuntu session on Windows...

I do have an ssh port open, however.  Would cygwin (a 'la "ssh -X me@mycomputer) work?

sigh.............

Anyway, the least amount of "my residue" (HEY!!!) on her computer the better......you know what I mean.

Thanks!

---

### Post by dmizer on 2009-07-28
This works well for me: [http://www.gnu.org/software/gnump3d/](http://www.gnu.org/software/gnump3d/)

```
sudo aptitude install gnump3d
```
Edit the /etc/gnump3d/gnump3d.conf file and change the "root =" variable so it points to your music folder.

Then browse to the Ubuntu machine with: [noparse]http://ubuntu-ip-address:8888[/noparse] in windows.

Windows media player will work just fine with that.

---

### Post by aaronLund on 2009-07-29
> **dmizer said:**
> This works well for me: [http://www.gnu.org/software/gnump3d/](http://www.gnu.org/software/gnump3d/)

```
sudo aptitude install gnump3d
```
Edit the /etc/gnump3d/gnump3d.conf file and change the "root =" variable so it points to your music folder.

Then browse to the Ubuntu machine with: [noparse]http://ubuntu-ip-address:8888[/noparse] in windows.

Windows media player will work just fine with that.

Wow.

This is really friggin cool!

Totally works.  

Do you know of any way to add a whole playlist though?

As it stands, out of the box, I can only add .m3u files one by one.  

Also, for the record, I am indeed using Songbird to play these (in Windows).  

Thanks!

---

### Post by aaronLund on 2009-07-29
Actually, I just figured out how to add a random playlist.....

There's a button on the bottom of the page.

This is awesome.  Thanks again.

---

### Post by dmizer on 2009-07-29
> **aaronLund said:**
> Actually, I just figured out how to add a random playlist.....

There's a button on the bottom of the page.

This is awesome.  Thanks again.

No problem!

BTW, there's also an option for a custom playlist :)

---

