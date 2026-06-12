---
title: "wierd fstab problem"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by Demented ZA on 2009-08-03
Hi All, 

A friend of mine has a notebook running Ubuntu 9.04.  On it I have set up shares via fstab to automount ntfs shares on a server system. It used to work flawlessly untill bout three days ago where it stopped automounting my shares.

I checked /etc/fstab but its still perfect.

When I do

```
sudo mount -a
```at the command prompt, it mounts the shares wrom fstab perfectly.

I tried adding a command to startup:

```
gksu mount -a
```But, after asking me for password, nothing happens. I also do
```
gksu mount -a
```from Terminal.

It asks me for password, after i type it in, I get taken to the next prompt without error. My shares still do not mount.

To summarize, only ```
sudo mount -a
``` works, and not 

```
gksu mount -a
```.

I can't use
```
sudo mount
```
as a startup command as it doesn't invoke the prompt for password. Its too much trouble for my friend to drop to a terminal and type the above.

Is there  a difference between gksu and sudo (I assume gksu is the Gnome GUI equivalent of sudo?)

I also guess my sollution lies somewhere in the answer to the above question.

How else do I get my shares to mount?

If its an update that broke something, how will i know?
Any help would be greatly appreciated.

---

