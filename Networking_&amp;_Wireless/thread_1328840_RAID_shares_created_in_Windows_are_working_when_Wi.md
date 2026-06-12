---
title: "RAID shares created in Windows are working when Windows isn't on"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by giyad on 2009-11-16
Ok, I'm not complaining, I'm just hoping someone can explain to me why this is working.

I have a RAID setup in Windows to share with my network.  I also have this RAID mounted in Ubuntu when I boot into it.  Right now I'm booted into Ubuntu, and I'm also sharing the same drive.  However, obviously the path has changed right?  Its no longer Z:\Media, now its /media/Z.  The shares are also from different computer names (Desktopz on windwos and desktopzubuntu on Ubuntu).

Now, I have an AppleTV and installed Boxee on it, and added my shares as sources.  In theory, I should have to add my Ubuntu RAID share as a source as well, since when I'm not booted into Windows, I shouldn't be able to access those files.  The IP is the same, that I understand, but the path has changed, and the computer names have changed.  On Ubuntu, I'm desktopzubuntu, and on windows im simply desktopz.

Why is it working?????  I didn't add the ubuntu shares in boxee, so why is it working?

Like I said I'm not complaining, but I'm not understanding the logic here...  If I'm not logged into Windows, the share can't be accessed, so why am I able to access it?!

**UPDATE - SOLUTION**

When adding the source or accessing the source from another location, make sure to use IP address instead of the computer name.  That was the problem, it would search for the computer name and since I was booted up in a different OS, the computer name was not the same.  When you use the IP, it just works!

---

### Post by gerowen on 2009-11-16
Spooky, lol.  Are the raid enclosures connected to the network, or only to the PC?

---

### Post by giyad on 2009-11-17
> **marcusdean.adams said:**
> Spooky, lol.  Are the raid enclosures connected to the network, or only to the PC?
haha seriously!  I can't figure this out, but its working so I'm not touching it :p

Its not a hardware RAID its via the motherboard so its a fakeRAID.  Honestly though, the headache it gave me to get the RAID to mount... this really is a reward haha... but still, I'd like to understand what the hell is going on.

What could it be?  When you create a windows share for a drive, does that info get saved somewhere?

---

### Post by giyad on 2009-11-17
Ok, so at least something is working as expected.  My shares don't show up on my Mac under the same name, so everything in iTunes is bringing up the error that Desktopz (computer name) can't be located and that the file can't be located.  This makes sense, so why is Boxee working differently... so weird.

Anyway, that brings up another question.  Is it possible to share the same file from two different Operating Systems (from the same drive at different times)?

---

### Post by giyad on 2009-11-17
I feel like an idiot right now... but no one who read this figured it out either ;-) haha... anyway... its because I had added my sources on Boxee via my IP instead of using computer name.  On my Mac my shares were being connected by computer name.

So, I guess its always safest to just use IP instead of any naming... from now on i'm typing 9.189.94.12 instead of ubuntuforums.org :P

---

### Post by gerowen on 2009-11-17
> **giyad said:**
> I feel like an idiot right now... but no one who read this figured it out either ;-) haha... anyway... its because I had added my sources on Boxee via my IP instead of using computer name.  On my Mac my shares were being connected by computer name.

So, I guess its always safest to just use IP instead of any naming... from now on i'm typing 9.189.94.12 instead of ubuntuforums.org :P

Well for public domains that's not "always" a safe bet, most companies have a static IP, but some don't and they just use a dynamic dns service to keep their domain name pointed to their current IP address.  That's what I do on dyndns.org so I can advertise my personal server with a domain name instead of keeping all my friends updated with my new IP address.  Neat how you got that rigged up though, :-)

---

### Post by giyad on 2009-11-18
yeah i was only joking about actually using IP from now on haha... but thanks :), yeah I'm loving how this stuff is working now!

---

