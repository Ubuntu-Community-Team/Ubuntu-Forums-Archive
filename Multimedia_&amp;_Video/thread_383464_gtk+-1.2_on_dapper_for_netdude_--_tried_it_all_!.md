---
title: "gtk+-1.2 on dapper for netdude -- tried it all !"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by ShackledMystic on 2007-03-13
Ok here goes :

im new to Ubuntu but have learned pretty much in the time tat ive spent wid it 

heres the issue -- i need to get "netdude" [network monitoring tool for debian] installed on my ubuntu dapper machine n i need to do it _***[COLOR="Red"]Real Urgently [/COLOR]***_

here are the problems ive faced "till date " : 

->netdude needs gtk+-1.2 -- the ubuntu release has newer version [netdude doesnt support gtk2 n i have the latest version o netdude]

->gtk+-1.2 requires the libglib or glib library >=1.2.8  --- this glib version has a tool names "glib-config" --- now dapper comes wid glib2.xx in which theres no glib-config -- i am unable to uninstall glib2.xx because all the gnome applications depend on it ! 

->ive tried installin both the version of glib -- tat is glib1.2.8 glib 1.2.10 n wht not -- they seem to get installed well -- but then when i configure gtk+-1.2 , it says that glib is not found

during the configuration o gtk the glib-config is found and its path is also shown in the lines tat appear -- so i guess the config finds glib-config BUT NOT glib itself !! :( :confused: 
[ my apologies for not pastin the lines tat appear - but trust me tats wht comes on there ] 




now ill let u kno wht i beg of all u ubuntu users out there : :KS 


--> Let me kno if NEONE has installed gtk+-1.2 [not gtk2] on their Dapper drake or ne other release ! 

--> Please send me links of correct versions of the libraries tat it needs [ive downloaded millions o versions o all the libraries needed n have gone almost mad sorting out the version conflicts :( 

--> let me kno if theres a release tat comes preinstalled wid the gtk+-1.2 toolkit :) 

[LAST BUT NOT LEAST -- I DONT HAVE INTERNET CONNECTION ]

so apt-get install wont work here :) -- i can download libraries and install them separately using other systems -- i cant get my internet to work on the ubuntu machine ! ive stopped trying tat ! 


thanks a milllllion -- pardon me if ive written sumin weird or incorrect -- im new to the forum scene -- thanks a lot

---

### Post by lloyd_b on 2007-03-13
I know nothing whatsoever about "netdude", but I do know a few things about gtk1/glib1.

There are 5 packages you need to install:
libgtk1.2 libgtk1.2-common libgtk1.2-dev libglib1.2 libglib1.2-dev

All of these should be on the installation CD, so you should be able to do an "sudo apt-get install ..." from the CD without needing an internet connection.

As for "unistalling glib2", that is NOT necessary.  Gtk1/Gtk2 and Glib1/Glib2 can coexist on the same system without any problems.  I'm currently running with both installed in Xubuntu Edgy, and have done the same with Ubuntu Edgy and Ubuntu Dapper.

Lloyd B.

---

### Post by ShackledMystic on 2007-03-14
eh maan lloyd thanks a lot 

i dunno if the libraries u listed were there on the cd or not ! 

i got the thing to work before i got ur reply ! wohooo i feel like ive achieved sumin 

heres wht i did [for neone who is facin similar trouble ]


--> i "sumhow" managed to get my internet to work on the Ubuntu hoary version ! 

--> used $sudo apt-get install [package name] to install the libraries n wht followed was smoother than steve vai on his guitar !!!:guitar: 

all the libraries got installed without a single error or conflict -- i installed netdude manually after tat using #./compile;make;make install

everythings working fine !!!! :) \\:D/ [ One can make out im havin fun wid the smileys eh ]

neways thanks everyone related to this forum 

happy ubuntuing !

---

