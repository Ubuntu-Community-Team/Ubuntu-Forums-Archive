---
title: "help protected network"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by skullomaniac on 2008-12-09
i had a person come over some time ago to protect my network
thing is once he was gone everything was working ok. that is my pc (with ubuntu) could connect to internet via wireless.
the guy set a static ip with a gateway ecc. on all the pcs i have at home (including this one).
now here comes the problem!! 
i switch off the computer and  next day i try to access the internet via wireless and... not working!!
something is wrong coz all the other pc's i have in this house (windows :( ) connect to the protected wireless network.
i when i check the network tools i see that he manually configured ip etc on this ubuntu pc... 

anyways at first not even the wired connection worked but i type history on the terminal to see if there were any interesting commands the guy used to set up the wireless connection on this pc 

here are the commands:

 >  

  189  su -
  190  sudo ifconfig -a
  191  sudo iwconfig
  192  ping [www.google.it](www.google.it)
  193  sudo iwconfig
  194  
  195  sudo ifconfig
  196  sudo iwconfig
  197  sudo iwlist
  198  sudo iwlist eth1
  199  ping 10.0.0.2
  200  ifconfig
  201  iwconfig
  202  iwlist eth1
  203  iwlist
  204  iwlist eth1 scanning
  205  iwconfig
  206  iwconfig eth1 10.0.[COLOR="Red"]rest of my ip has been omitted[/COLOR] up
  207  iwconfig eth1 up
  208  iwconfig eth1sudo /etc/init.d/networking restart
  209  /etc/init.d/networking restart
  210  cd /etc/
  211  ls
  212  cd network/
  213  ls
  214  vi interfaces
  215  sudo vi interfaces
  216  sudo /etc/init.d/networking restart
  217  iwconfig
  218  iwconfig --help
  219  man iwconfig
  220  ls
  221  ifconfig
  222  route -n
  223  ping [www.google.it](www.google.it)
  224  route del 169.254.0.0
  225  sudo route del 169.254.0.0
  226  sudo route del 169.254.0.0 eth1
  227  sudo route del default gw
  228  sudo route del gw 
  229  sudo route del 169.254.0.0
  230  route -n
  231  ping 10.0.0.2
  232  ping 10.0.0.231
  233  ping 10.0.0.232
  234  ping 10.0.0.231
  235  ping [www.google.it](www.google.it)
  236  iwconfig
  237  iwconfig 
  238  sudo /etc/init.d/networking restart
  239  wireless
  240  sudo wireless
  241  iwspy
  242  iwconfig 
  243  iwconfig
  244  iwconfig --help
  245  iwconfig eth1 essid on
  246  iwconfig eth1 essid galpi
  247  sudo iwconfig eth1 essid galpi
  248  iwconfig
  249  sudo iwconfig eth1 10.0.[COLOR="Red"]rest of ip has been omitted[/COLOR]
  250  sudo iwconfig eth1 essid on
  251  iwconfig
  252  ifconfig eth1 up
  253  sudo ifconfig eth1 up
  254  iwconfig
  255  ifconfig
  256  ping [www.google.it](www.google.it)
  257  iwconfig eth1
  258  iwconfig
  259  iwconfig -h
  260  sudo iwconfig eth1 commit
  261  sudo ifconfig eth1 10.0.[COLOR="Red"]rest of ip omitted[/COLOR]
  262  ifconfig
  263  sudo /etc/init.d/networking restart
  264  ifconfig
  265  ifconfig eth1 up
  266  sudo ifconfig eth1 up
  267  ifconfig
  268  iwconfig
  269  sudo ifconfig
  270  sudo dmesg
  271  ifconfig
  272  sudo route -n
  273  ping [www.google.it](www.google.it)



as i said not even the wired connection worked but when i type in terminal command 209 the wired connection works again

how do i solve this problem??
i want to connect to the wireless network again and to the wired network without having always having to type commann 209 again...

---

