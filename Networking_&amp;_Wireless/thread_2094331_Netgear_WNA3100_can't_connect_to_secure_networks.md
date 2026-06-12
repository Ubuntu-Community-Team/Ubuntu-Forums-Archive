---
title: "Netgear WNA3100 can't connect to secure networks"
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by jomasdf on 2012-12-13
Hello.

I just completed installing the drivers for this device, took some time but seems to be working fine now. No problems with connecting to networks, however, trying to connect to one that has a password is really wierd.

A box pops up and tells me that the password didn't work. And it doesn't matter how many times I try, allways the same.

Does anyone have a clue to how this can be fixed? A work around?

Thanks.

Found this: [http://sourceforge.net/p/ndiswrapper/patches/29/?page=1](http://sourceforge.net/p/ndiswrapper/patches/29/?page=1)

                               The following patch will allow the  Ndiswrapper to install the Broadcom driver BCMWLHIGH5.inf supporting the  WNA3100 wireless wlan adapter. 
 Add the following to ntoskernal_io.c
 wstdcall NTSTATUS WIN_FUNC(IoUnregisterPlugPlayNotification,1)
    (void [I]tag)
{
    TRACE2("%p", tag);
    TODO(); /[/I] Probably Not, legacy function abandoned in Windows 7 [I]/
    IOEXIT(return STATUS_SUCCESS); /[/I] Linux doesn't use it either */
}
 To support NetGear WNA3100 USB 802.11n

    
            

Might this help me and how to I do this ?

---

