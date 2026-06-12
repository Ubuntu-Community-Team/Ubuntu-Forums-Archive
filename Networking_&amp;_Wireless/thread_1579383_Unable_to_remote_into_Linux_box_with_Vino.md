---
title: "Unable to remote into Linux box with Vino"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by Zubatron on 2010-09-21
I have Ubuntu 10.04 installed on an older desktop and when I first installed Ubuntu I set up Remote Desktop Vino services and was able to connect just fine with my Windows XP, Windows 7, Leopard, Snow Leopard PCs and my iPhone using VNC all just fine.

So I apply updates to my Linux box and now it's broken. I can not remote into my Ubuntu machine at all now. So something with the updates is broken.
I don't really use my Ubuntu machine at all, all it is used for is for a dedicated Folding@Home server. I attached a screenshot as what my Remote Desktop settings look like. Please help!

---

### Post by Zubatron on 2010-09-22
bump

---

### Post by Zubatron on 2010-09-22
sigh.....another bump

---

### Post by Zubatron on 2010-09-23
once again another bump....seriously, no help here?

---

### Post by Zubatron on 2010-09-23
Ok, this is getting to the point of ridiculousness. No response at all? I know plenty of people are looking! Basically I want to know if Canonical knows of this bug and is going to fix it or if there is another way around it (besides having to install another remote software which I am not interested in doing. Why? Because that's the same as having Microsoft Word breaking from a Windows update and Microsoft tells you to go use Openoffice instead!). Yes I am sounding bitter but this small problem is just so minute that not being able to find anything from online nor within the community and the lack of response is frustrating!

This is why people steer clear from Linux, not just due to having to learn a new OS but lack of support.

---

### Post by Zubatron on 2010-09-24
This is sad, I feel abandoned by the Linux community and this is sad that I have such a small problem yet no response after 3 days. 

I have looked up this problem on my own and do not wish to use another program besides Vino. I know any one looking at this is not going to care but I am going to wipe my Linux machine over the weekend and go back to an OS that is reliable and actually has a community that will actively support it. Yes, I am referring to Windows.

---

### Post by CharlesA on 2010-09-24
Stupid question but were you logged in when trying to connect? vino doesn't start unless you are logged in to the console.

Is the computer name actually "localhost" ??

Attached is what my remote desktop settings look like and I can connect fine.

I am running Lucid x86, with all updates.

---

### Post by NFAD on 2010-09-24
I am getting the same error after the updates, and I cannot find a solution.

PLEASE HELP!!!

---

### Post by CharlesA on 2010-09-24
What version of Ubuntu are you running?

Can you post the output of this please:

```
ifconfig
```

---

### Post by NFAD on 2010-09-24
> **charlesa said:**
> what version of ubuntu are you running?

10.04

> can you post the output of this please:

```
ifconfig
```

My network looks fine, it must be an update issue.  I uninstalled vino and reinstalled it.  This is even a clean new install and vino was working fine until i updated the new install.  If you still want to see ifconfig let me know.

---

### Post by CharlesA on 2010-09-24
Could you post what the remote desktop settings look like? Does it say "localhost" like the OP?

I updated my test desktop and was able to connect via vnc after logging into it.

---

### Post by Hobgoblin on 2010-09-24
> **NFAD said:**
> 
My network looks fine, it must be an update issue.  I uninstalled vino and reinstalled it.  This is even a clean new install and vino was working fine until i updated the new install.  If you still want to see ifconfig let me know.

If you are having exactly the same problem (i.e. your host is showing as localhost) then yes.

---

