---
title: "Small but slightly frustrating wireless bug"
date: 2007-10-12
forum: Mythbuntu
---

### Post by propagandhi on 2007-10-12
I have a Dlink usb adapter, its a DWL-G122 or something.

It works fine, was detected in mythbuntu straight away, I used the network manager in xfce/mythbuntu to go in a set the encryption mode to wpa2 personal and put the password in.

I ok to this and apply it, and my wireless runs beautifully.

However, if i reboot the machine, the wireless does not automatically connect, I go back into the network config and initially it will display as though its on WPA2 and the password is in there. I close this, then go back in and see that it says WPA Personal (not WPA2) and the password is blank.

I put it back on WPA2 and put the password in, and then I have my wireless working again!!

Any help?? Also thought it'd be good to report in case it can be patched up before final.

---

### Post by superm1 on 2007-10-12
Is this the only network you ever connect to?

If so, then click the wireless icon and choose manual connection.  You can configure permanent settings there.

---

### Post by propagandhi on 2007-10-12
Yep, this is at my home, I've got two myth combined backend/frontend systems both running mythbuntu ( I posted my two hardware configs a minute ago).

The box in my bedroom is the one with the wireless issue, the one in my lounge room is wired with gigabit ethernet, so I can't confirm whether its just the specific hardware at this stage.  I will do what you've suggested the second I get home from work.

Thanks a lot.

---

### Post by superm1 on 2007-10-12
Well the issue at hand unfortunately affects both Ubuntu and Mythbuntu.  It's because the password gets stored to a gnome keyring.  In order to access that keyring, you need to actually login to the box (not automatic login).  To automatically unlock it, you need libgnome-pam-keyring installed and to have your password that you login with set to the same as your keyring password.

If you can configure it using manual configuration, you should be able to avoid these problems.

---

### Post by propagandhi on 2007-10-12
Excellent, thank you very much for your prompt and informative response. I'm just wondering if you ever find time to sleep....

---

### Post by laga on 2007-10-12
> **propagandhi said:**
> I'm just wondering if you ever find time to sleep....

Most of the developers wonder about that, but we try not to wonder too much - just appreciate it :)

---

