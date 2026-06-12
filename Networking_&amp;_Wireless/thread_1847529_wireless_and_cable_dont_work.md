---
title: "wireless and cable dont work"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by zmezm14 on 2011-09-20
hi there
am using ubuntu 9.10 on HP G 60 laptop , am not able to connect to the internet , through wireless or cable , the problem happen after i install the " Kwaln " program ..
even when i removed the program , my network cared is not found or disabled, how can i fix this issue ..

thank you :KS

---

### Post by Bucky Ball on 2011-09-20
9.10 is no longer supported. I suggest you upgrade to the current stable release, 10.04 LTS. ;)

You might try right clicking the network icon and making sure 'Enable Network' is still ticked. I don't know what Kwain is but maybe that has changed your host/network settings. Right click the icon and 'Edit Networks' and see if anything has changed there. 

I would really think about an upgrade, though. 9.10 might be stable for you, for now, but there are no security updates for it anymore and that is not good.

Release cycle here:

[http://www.markshuttleworth.com/wp-content/uploads/2008/05/ubuntu-release-cycle.png](http://www.markshuttleworth.com/wp-content/uploads/2008/05/ubuntu-release-cycle.png)

---

### Post by zmezm14 on 2011-09-20
> **Bucky Ball said:**
> 9.10 is no longer supported. I suggest you upgrade to the current stable release, 10.04 LTS. ;)


am afraid i can't do that , because instead ns-2 simulator on it , and am not sure if i upgrade it will still work ..
i just want my network card to work again , it was working before i instell kwaln program

---

### Post by Bucky Ball on 2011-09-21
Good luck with it then, and good luck with your security issues. There is one way to find out if ns-2 will work ... google. If it works in 9.10 why wouldn't it work in a newer release???

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8CCZnlOJGQANF436At.;_ylc=X1MDMjExNDcwOTU1OQRfcgMyBGFvAzAEZnIDYWx0YXZpc3RhBGhvc3RwdmlkA2QwNWZyYmV4VTdmSDJncjdUTFR2NWcwYU9xRFVNazU1Wm9JQUNJUmcEbl9ncHMDMARuX3ZwcwMwBG9yaWdpbgNzcnAEcXVlcnkDbnMtMiBzaW11bGF0b3IgMTAuMDQEc2FvAzEEdnRlc3RpZAM-?p=ns-2+simulator+10.04&fr2=sfp&fr=altavista&rd=r1](http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8CCZnlOJGQANF436At.;_ylc=X1MDMjExNDcwOTU1OQRfcgMyBGFvAzAEZnIDYWx0YXZpc3RhBGhvc3RwdmlkA2QwNWZyYmV4VTdmSDJncjdUTFR2NWcwYU9xRFVNazU1Wm9JQUNJUmcEbl9ncHMDMARuX3ZwcwMwBG9yaWdpbgNzcnAEcXVlcnkDbnMtMiBzaW11bGF0b3IgMTAuMDQEc2FvAzEEdnRlc3RpZAM-?p=ns-2+simulator+10.04&fr2=sfp&fr=altavista&rd=r1)

There seems to be no problem with it in 10.04 LTS so maybe you should investigate. The version you have working in 9.10 is not the latest anyhow, perhaps?

This took me two seconds to find. It's this easy:

[https://launchpad.net/~wouterh/+archive/ppa](https://launchpad.net/~wouterh/+archive/ppa)

---

### Post by Bucky Ball on 2011-09-21
_... posted in error, :)_[]("http://www.photoblog.gmkwainphoto.com/?category_name=portraits")

---

### Post by Bucky Ball on 2011-09-21
Simple as this:

[http://ubuntuforums.org/showthread.php?t=1450346&page=1](http://ubuntuforums.org/showthread.php?t=1450346&page=1)

The solution in post #2. Kwlan uninstalled Network Manager by the looks.

This solution took seconds to find. *Please* search before posting. ;) Here are more clues if that doesn't work:

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8O2aXlO80IAKV436At.;_ylc=X1MDMjExNDcwOTU1OQRfcgMyBGFvAzAEZnIDYWx0YXZpc3RhBGhvc3RwdmlkA2pkUnhPcmV4VTdmSDJncjdUTFR2NWcwek9xRFVNazU1YWJZQURQckwEbl9ncHMDMARuX3ZwcwMwBG9yaWdpbgNzcnAEcXVlcnkDdW5pbnN0YWxsIGt3bGFuIG5vIG5ldHdvcmsgdWJ1bnR1BHNhbwMxBHZ0ZXN0aWQD?p=uninstall+kwlan+no+network+ubuntu&fr2=sfp&fr=altavista&rd=r1](http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8O2aXlO80IAKV436At.;_ylc=X1MDMjExNDcwOTU1OQRfcgMyBGFvAzAEZnIDYWx0YXZpc3RhBGhvc3RwdmlkA2pkUnhPcmV4VTdmSDJncjdUTFR2NWcwek9xRFVNazU1YWJZQURQckwEbl9ncHMDMARuX3ZwcwMwBG9yaWdpbgNzcnAEcXVlcnkDdW5pbnN0YWxsIGt3bGFuIG5vIG5ldHdvcmsgdWJ1bnR1BHNhbwMxBHZ0ZXN0aWQD?p=uninstall+kwlan+no+network+ubuntu&fr2=sfp&fr=altavista&rd=r1)

---

### Post by zmezm14 on 2011-09-21
> **Bucky Ball said:**
> Simple as this:

[http://ubuntuforums.org/showthread.php?t=1450346&page=1](http://ubuntuforums.org/showthread.php?t=1450346&page=1)

The solution in post #2. Kwlan uninstalled Network Manager by the looks.

This solution took seconds to find. *Please* search before posting. ;) Here are more clues if that doesn't work:

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8O2aXlO80IAKV436At.;_ylc=X1MDMjExNDcwOTU1OQRfcgMyBGFvAzAEZnIDYWx0YXZpc3RhBGhvc3RwdmlkA2pkUnhPcmV4VTdmSDJncjdUTFR2NWcwek9xRFVNazU1YWJZQURQckwEbl9ncHMDMARuX3ZwcwMwBG9yaWdpbgNzcnAEcXVlcnkDdW5pbnN0YWxsIGt3bGFuIG5vIG5ldHdvcmsgdWJ1bnR1BHNhbwMxBHZ0ZXN0aWQD?p=uninstall+kwlan+no+network+ubuntu&fr2=sfp&fr=altavista&rd=r1](http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8O2aXlO80IAKV436At.;_ylc=X1MDMjExNDcwOTU1OQRfcgMyBGFvAzAEZnIDYWx0YXZpc3RhBGhvc3RwdmlkA2pkUnhPcmV4VTdmSDJncjdUTFR2NWcwek9xRFVNazU1YWJZQURQckwEbl9ncHMDMARuX3ZwcwMwBG9yaWdpbgNzcnAEcXVlcnkDdW5pbnN0YWxsIGt3bGFuIG5vIG5ldHdvcmsgdWJ1bnR1BHNhbwMxBHZ0ZXN0aWQD?p=uninstall+kwlan+no+network+ubuntu&fr2=sfp&fr=altavista&rd=r1)


thank you sir appreciate the effort , and so the sarcasm :?, but mostly the help , mostly ..

---

### Post by Bucky Ball on 2011-09-21
;) Did it work? Easiest way to go System>Administration>Synaptic Package Manager, then search for 'network manager gnome' (if you are using gnome, that is). Install and you should be done. If that doesn't work reboot and see if you're back in business.

---

### Post by zmezm14 on 2011-09-21
> **Bucky Ball said:**
> ;) Did it work? Easiest way to go System>Administration>Synaptic Package Manager, then search for 'network manager gnome' (if you are using gnome, that is). Install and you should be done. If that doesn't work reboot and see if you're back in business.

thank you , sir for your help ..:)

---

