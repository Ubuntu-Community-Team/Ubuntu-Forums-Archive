---
title: "Unsupported video card is really supported"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by fakie_flip on 2007-05-26
Hello, I am trying to get a driver for my video card to have 3d acceleration for games and compiz. When I try to use the Restricted Driver Manager in Ubuntu, it says my video card is not supported. Also this wiki page says my card is not supported by the ati linux driver.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATIhttps://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATIhttps://help.ubuntu.com/community/BinaryDriverHowto/ATI)

> The model of the card is in the 9xxx series, 9500 or higher, or it is in the X series (e.g. X300), or it has TV-Out capability. The 'fglrx' driver does not support cards earlier than the 9500.

lspci:
```
winston@kubuntu:~$ lspci | grep ati
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
winston@kubuntu:~$
```

However when I use Korora XGL Live CD that has the nvidia and ati drivers installed in it already, my ati 64 megabyte video card works good with the driver in it. I can spin the cube without any lag at all and see the visual effects of xgl and compiiz. How can I get the same thing in Ubuntu? I've thought of installing Kororaa, but I'd really like to get 3d acceleration working in Ubuntu.

---

