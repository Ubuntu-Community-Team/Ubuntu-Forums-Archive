---
title: "Mapping a windows Desktop drive over network to ubuntu system"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by livin4th on 2012-04-20
Hi,
           I have a windows desktop at work and I have a ubuntu 10.04 on my laptop at home. I want to access the files on my desktop using my laptop when at home. I heard the partitions in windows can be mapped to ubuntu and can be accessed over the network. I tried looking it up online but all the blogs mentioned that the mapping can only be done if the windows is a server desktop. Is it true that only windows server partitions can be mapped to ubuntu over the network or can any normal desktop partition can be mapped? If it is possible, can some one point me to a link where I can learn how to do that.

Thanks in advance,
Livin

---

### Post by newbie-user on 2012-04-20
You can connect to the Windows desktop as long as you have already created shares. Then on the Ubuntu laptop, you just click on "Places" on the panel, the "Connect to Server", and fill in the name of the server and share, and choose "Windows Share" as the type of share. Ignore the username and password until the next dialog box.

The Windows machine doesn't have to be an actual server as long as your shares are set up correctly.

---

