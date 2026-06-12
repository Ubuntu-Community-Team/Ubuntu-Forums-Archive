---
title: "Sprint 3G/4G U301 modem not working under 10.10"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by yyyc186 on 2010-10-26
Hello,

Today I wiped my notebook and installed AMD 64-bit KUbuntu 10.10.  Previously with 10.04 my Sprint U301 modem worked just fine, but I did not write down any settings.  I trusted memory #777 user user.  I find documentation on-line which still says this should work, but it certainly doesn't fly with 10.10.  I can reboot the notebook using the icky Windows Worsta partition and all is well with the modem.

Has anyone gotten the U301 modem to work under 10.10 KUbuntu?  If so, what settings did you use?

---

### Post by ezphilosophy on 2011-04-11
I did exactly what you mentioned and it worked.

New Broadband Mobile connection
CDMA
Number: #777
Login: user
Password: user
And I checked "Connect Automatically"

With Kubuntu 10.10, it asks you if it is a CDMA or GSM connection.  I assume you picked CDMA?  Mobile Broadband?

If it still doesn't work, try to set it up using KPPP.  I first got it working in there and then realized that putting in the username and password in the Network Management applet could work too, and it did.

I assume you got it working as this post is over 6 months old but others will stumble on this post when they google u301 and Kubuntu.

---

