---
title: "NetworkManager Applet"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by iisjman07 on 2008-12-06
Hello everyone on the ubuntu forums!
My problem (if it can be called a problem) is that whenever I turn on my PC, I get a little box popup asking me to type in my password. It said something about a 'NetworkManager Applet'. Until this is done the computer will not connect to any wireless networks...

---

### Post by mariane_08 on 2008-12-06
Hi,

I'm struggling with the same problem!!!! Most anoying. You'll se my thread under "nm aplet and default keyring?"

It was suggested to me that this can happen your login password and keyring passwords are different. But I changed them so they are same and it still happens. If I find out a resolution I'll sure let you know.Hopefully soon!

---

### Post by kojo on 2008-12-06
I only had this occur on my machine once I enabled automatic login under the security tab of the login window preferences (Ubuntu 8.10 Sony VGN-FZ145E).

Prior to automating the login the popup did not appear.  I understand the situation to be that the keyring needs your password so that it can login to a secured wireless network.

> **mariane_08 said:**
> Hi,

I'm struggling with the same problem!!!! Most anoying. You'll se my thread under "nm aplet and default keyring?"

It was suggested to me that this can happen your login password and keyring passwords are different. But I changed them so they are same and it still happens. If I find out a resolution I'll sure let you know.Hopefully soon!

---

### Post by MontisCalpe on 2008-12-06
I have just worked out how to stop this happening.

 Delete file:///home/(insert your user name here)/.gnome2/keyrings/default.keyring

you will have to access your files in root

sudo nautilus

and show hidden files (view at top of page and put tick in "show hidden files" box).

Restart your pc

This resets your keyring password.

When restarted you will be prompted to re enter your keyring/ wireless login passwords.

ENTER ONLY YOUR PASSWORD THAT CONNECTS YOU TO YOUR ROUTER. this is the first password you are asked for. When asked for the second password - leave the field blank and press return.

You will be given a security warning but continue.

Restart your pc and you will connect to your wireless network without password prompt.

This worked for me and took some time to figure out. Who would have thought it so easy. 

I have been using Linux for only 2 weeks

Hope this works for you?

---

### Post by mariane_08 on 2008-12-07
Unfortunaely this doesn't work for me :frown:

And I don't seem to have a file "default keyring" in /gnome2
just "login keyring"

I beginning to wonder if there's something weird and unique to my system? I begining to think it might be time for a re-install. I was thinking about installing intrepid anyway. I've asked this question so many places now and there seems to be no solution! 

> **MontisCalpe said:**
> I have just worked out how to stop this happening.

 Delete file:///home/(insert your user name here)/.gnome2/keyrings/default.keyring

you will have to access your files in root

sudo nautilus

and show hidden files (view at top of page and put tick in "show hidden files" box).

Restart your pc

This resets your keyring password.

When restarted you will be prompted to re enter your keyring/ wireless login passwords.

ENTER ONLY YOUR PASSWORD THAT CONNECTS YOU TO YOUR ROUTER. this is the first password you are asked for. When asked for the second password - leave the field blank and press return.

You will be given a security warning but continue.

Restart your pc and you will connect to your wireless network without password prompt.

This worked for me and took some time to figure out. Who would have thought it so easy. 

I have been using Linux for only 2 weeks

Hope this works for you?

---

### Post by MontisCalpe on 2008-12-07
Sorry, 

did not realize you were not using Intrepid. I would recommend installing this and then try my tip

---

