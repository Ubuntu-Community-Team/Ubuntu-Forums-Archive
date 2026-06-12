---
title: "Can see, but can't connect to work wired network"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by nitroguy on 2009-06-18
Hi there.

I just installed 9.04 on my work desktop machine, but after realizing a program I needed was best supported by 8.04, I installed that in 9.04's place.

My issue is this: when I had 9.04, I clicked on Network, and could see my work's network, computers, etc; but when I clicked on something it asked for my user and password (for the network, not ubuntu). But now, in 8.04, it doesn't authenticate, it just shows me all the computers on the network, but no computer has any files inside of it.

So, my question: can I manually authenticate, something that was automated for 9.04, but must be done by hand in the older release?

Thanks.

nitroguy

---

### Post by swerdna on 2009-06-18
> **nitroguy said:**
> Hi there.

I just installed 9.04 on my work desktop machine, but after realizing a program I needed was best supported by 8.04, I installed that in 9.04's place.

My issue is this: when I had 9.04, I clicked on Network, and could see my work's network, computers, etc; but when I clicked on something it asked for my user and password (for the network, not ubuntu). But now, in 8.04, it doesn't authenticate, it just shows me all the computers on the network, but no computer has any files inside of it.

So, my question: can I manually authenticate, something that was automated for 9.04, but must be done by hand in the older release?

Thanks.

nitroguy

That sounds vaguely like a Nautilus bug whereby you can't drill down to see the shares under the computer icon in Nautilus. Here's the bug report:
[http://bugzilla.gnome.org/show_bug.cgi?id=524485](http://bugzilla.gnome.org/show_bug.cgi?id=524485)

Check out your version of Nautilus and see if it's 2.22.2 through 2.22.5. If it's not then this is not the problem. If it is then check out the updates and read the bug report for a fix. I was never able to fix it in my Nautilus until I changed to Ubuntu 9.04 (but then that's probably because I'm a newbie).

---

### Post by nitroguy on 2009-06-18
hmmm... I'ts Nautilus 2.22.5.1 - Does that mean I'm affected?

Is is possible to upgrade nautilus without upgrading the entire OS?

---

### Post by swerdna on 2009-06-18
> **nitroguy said:**
> hmmm... I'ts Nautilus 2.22.5.1 - Does that mean I'm affected?

Is is possible to upgrade nautilus without upgrading the entire OS?

Here's how to check if you're affected:
Put the address of a real share into the nautilus address bar, like this:
smb://servername/sharename/

If the contents of the share appear, then you're affected. So see if you are affected before we go on.

---

### Post by nitroguy on 2009-06-18
You'll have to excuse me, but I'm a bit new to this game (especially the networking side). 

What's a "real share" and how/where do I put it?

---

### Post by Iowan on 2009-06-18
Most of the options under Places invoke Nautilus in some form - or you can type **nautilus** on a command line.

---

### Post by doas777 on 2009-06-18
> **nitroguy said:**
> You'll have to excuse me, but I'm a bit new to this game (especially the networking side). 

What's a "real share" and how/where do I put it?

an address on a windows network (when on a linux box), is done in the form of:
```

smb://servername/sharename

```by real share swerdna means that you should specify the sharename like above. 
when you browse a computer via gnome, it will show you all the shares. this bug prevents the user from browsing the computer, but if the user specifies the share manually, it will allow you in.

so just put an address like the one above into nautilus, and see if it lets you in then. just go to places -> network, and then in the address bar at the top, put in an address like the one swerdna suggested.

good luck

---

### Post by swerdna on 2009-06-18
Just to be completely explicit, here's an example. Look at the screenshot of Nautilus looking across the LAN into a Linux share on a Suse computer on my LAN:
[[COLOR="Red"]Click this link to see the pic[/COLOR]]("http://www.swerdna.net.au/forumpics/ubuntupic.png")
That shows a share with the network name "linuxshare" in the computer with the server name "suse111", from which the address in Linux terminology is
smb://servername/sharename = smb://suse111/linuxshare.

Get the drift?

---

### Post by nitroguy on 2009-06-19
Yeah, that makes good sense. I'll have to try it.

To be honest, I ran into another issue with LTS, so I jumped back up to 9.04, and i'm golden again.

But I think I'll play around with shares and servers and stuff to get the hang of things a bit better. You'll probably see a bit more of me in this forum.

Thanks again guys for your help!

---

