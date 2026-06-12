---
title: "installed ndiswrapper then removed. cant reinstall card"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by socksfelloff on 2009-07-09
hey guys, new to ubuntu and loving it so far. the only issue i have had is getting my wireless to work.
a little history:
asus g1s laptop
installed ubuntu, it saw the card as wlan0 ( intel 3945 card) and i was able to see networks threw another program however could never do it in ubuntu. so i figured i must need to install a proper driver using ndiswrapper however that made the card not work at all. before when i right clicked on the network icon at the top i had to option to enable and disable wireless. now its gone. so i did "iwconfig" and it doesnt show my wireless anymore.

so i uninstalled ndiswrapper however i cant figure out how to reinstall the stock drivers the ubuntu put on, i think now my problem was with the gnome network manager, i cant figure out how to load that up either lol. any help on reinstalling my wireless card back to default would be greatly appreciated!

---

### Post by superprash2003 on 2009-07-10
post output of the following from the terminal
1)lshw -C network
2)iwconfig

---

