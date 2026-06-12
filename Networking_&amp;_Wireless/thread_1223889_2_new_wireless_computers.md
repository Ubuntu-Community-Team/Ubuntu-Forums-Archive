---
title: "2 new wireless computers"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by GNUway Tech on 2009-07-26
I have 2 new computers I'm trying to setup in my network to run wirelessly. 1 of them will be running a Belkin F5D7050 USB Network adapter, which a lot of people on this forum say they have no trouble running. The other one has an internal wireless card in it, and I don't know what kind it is.

I've never ran a wireless network on Kubuntu before, so I have no idea how to do it. I understand that the drivers are different by the wireless adapter, so my 1st step would be to find out what kind of wireless card is in the 2nd computer. How do I do that???????

I need someone to tell me everything I need to know about how to make these computers run wirelessly, As I said, I've never done this on Kubuntu, so I don't have the 1st clue how.:confused:

---

### Post by GNUway Tech on 2009-07-27
Okay, so I've done some more researching and figuring out. The wireless card in the 2nd computer is a Linksys WMP54Gv4, which uses the RaLink RT2500 chipset. That answers that question. Check.

After taking the computer apart to figure that out, I decided to try using ndiswrapper with the Windows Wireless Drivers GUI. I figured out how to download the .exe driver file from Linksys, unzip it, and install the rt2500.inf driver in Windows Wireless Drivers. Check.

Now, every time I open Windows Wireless Drivers, it tells me it can't tell if the hardware is available. But, in the little screen, to the left, listing the installed drivers, it says hardware available, yes.

What else do I have to do????????? Is there a simpler way to make this work????????

---

### Post by GNUway Tech on 2009-07-27
Okay, new developments. The network manager is picking up my network now. It's actually listing out nearby networks, and, when I click on mine, it will ask me for the access key. But, it still won't let me sign in.:popcorn:

I'll punch in the access key, and it'll give me a message advising me to save the access key in a wallet. I don't feel like doing that, so I hit cancel. It tells me that the connection failed. I tried saving the wallet, and it just kept saying that it was waiting for authorization.:confused:

I waited for about 5 minutes for it to connect and got tired of waiting. I closed the wallet and got a message that the connection failed. It's still listing my network in the network manager and giving me the option to sign in. It just won't connect.

What do I do???????????

---

### Post by RedSingularity on 2009-07-27
Are you entering the correct encryption type for the network?

---

### Post by GNUway Tech on 2009-07-27
Yes, I know the encryption type on my network.

That's not the problem though. I just found the problem. I'm entering the wrong access key. Sorry for any confusion and thanks for bearing with me.

---

