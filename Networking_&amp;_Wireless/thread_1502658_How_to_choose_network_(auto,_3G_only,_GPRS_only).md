---
title: "How to choose network (auto, 3G only, GPRS only)"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by astrocoder on 2010-06-05
hello, :)
I'm using Sierra Wireless AT&T USB wireless modem. My problem my modem automatically choose the network for me. I have 3G access in the area where i live but with unknown reason my modem choses GPRS speed (which is ridiculously slow). I used to be using MacOS X Snow Leopard (now i'm fully migrated to Linux) and there are special software provided by AT&T that allow me to choose preferred network either "3G Only", "GPRS Only" or "Auto". Now i think the setting in linux is at "Auto" state because the modem chooses the network automatically for me (by choosing GPRS network on 3G available area). How can i change it to "3G only" network so i can use internet at 3G speed all the time?

PS: Sorry, i'm not very good in english :)

---

### Post by alexfish on 2010-06-05
hi

may depend on the type of modem ZTE and Huawie have different AT commands

there is a doc for sierra wireless here it will auto download

[http://www.sierrawireless.com/resources/documents/support/2130617_Supported_AT_Command_Reference-v2.4.pdf](http://www.sierrawireless.com/resources/documents/support/2130617_Supported_AT_Command_Reference-v2.4.pdf)

---

### Post by astrocoder on 2010-06-05
wow, thankyou. i think i've found what i need :) but where can i use this AT command? how to send it to the modem?

---

### Post by alexfish on 2010-06-05
hi

sometimes you can use in the init codes of the likes of wvdial , gnomeppp a front end of wvdial  would be the best if you want to change the way the modem behaves  on a regular basis , place the AT commands at the start of the Inits , as for a serial terminal I find the best serial port terminal for Ubuntu is moserial

---

### Post by astrocoder on 2010-06-06
i have tried using minicom to communicate with my modem (/tty/ttyUSB04) and it doesn't give any output/replies. where can i read more about this procedure?

---

### Post by alexfish on 2010-06-06
hi

for minicom docs from the terminal 

code:

Man minicom

 as mentioned above , if your a novice install "moserial" the interface is easy to use, it will detect the ports automatically and has a user friendly input box
have a look in syaptic package manager or search web , it's a gnome application

or try gtkterm

---

### Post by astrocoder on 2010-06-06
at last, i have done it using minicom :) by using command at!selrat=01 i've set my modem to UMTS 3g only network. thankyou very much alexfish :) um.. one more thing, is this setting permanent or i have to do this everytime i power up the modem? :)

---

### Post by malmsteen84 on 2010-06-19
guys,

i am experiencing almost same problem here. i installed 10.04 recently and cant(?) send any at commands through minicom. example :

i run = $ minicom -o

then i must type ^A E (toggle echo) twice to get what i typed be shown on screen.

then begin typing = ATI
minicom response is = 
Sierra Wireless, Inc.                                                           
C885                                                                            
APP2 
(one line feed here)
OK

any commands starting with "AT" will result =
(one line feed here)
OK

any commands not starting with "AT" will result =
(one line feed here)
 ERROR
 
no response mentioning about band/gsm info, network type, etc.

fyi, i used to use 9.04 and minicom works fine =
turn on/off the modem using AT+CFUN,
set band to 3g only, auto, 2g only, etc easily, 
get info of network comprehensively, etc

do you guys have any idea about this? are the responses "hidden" or something? 
any suggestions I will very appreciate it.

---

### Post by alexfish on 2010-06-19
Hi

There is an easy to use serial terminal called moserial

have a look in synaptic 

It has an easy to use setup and a separate input box to which Typo errors can be corrected before sending to the modem

regards

alexfish

---

### Post by malmsteen84 on 2010-06-20
hi alexfish,
will give moserial a try. =====> sorry not working, it behaves like the minicom (can only give responses "OK" or "ERROR")

but still want to solve the minicom thing.... anyone?

---

