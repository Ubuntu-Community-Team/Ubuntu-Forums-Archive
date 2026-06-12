---
title: "Install netgear wgn311 card"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by Bill-in-Atlanta on 2009-09-07
although it has been slow going I am making progress on installing a netgear
card in unbuntu

right now I am trying to extract the netgear file ....
/home/god/Desktop/wg311_1_3.zip

but instead of getting the files i expect and already have in windwos i get the
following 

/home/god/Desktop/WG311_v30043_AdvSecurity_31219.exe (2)

which is a mystery to me and apparently to google..there's something in Frenc about it
whcih was not helpfull at all to me

is there unway to extract/open or whatever THAT file to get to the info isnide i need..drivers,inf file etc???????

anyway...I want the netgear files from the archive to get the inf to get ndiwrapper
to assocaite it with the card.e.tc...but the file i am getting i useless..nothing seems
to be able to open it..SO WHAT IS IT ANYWAY? 

the main question i show to i unzip the original file to give me the drives and inf
file i crave?

also another solution would be to use the one i have in xp...SO ..

IS THERE ANYWAY TO GET UBUNTU TO SEARCH ALL MY HDS FOR A STRING?

anyway help..and prayers woudl be appreciated

I am new to Linux..and I have a very strong constituion and cuss a lot

sorry for the typos but too tired right now to go back and correc tthem and also
this font is so small i cannot read it well

Bill-in-Atlanta

---

### Post by chili555 on 2009-09-07
Please connect with an ethernet cable and open a terminal and do:```
sudo apt-get install unshield
unshield x WG311_v30043_AdvSecurity_31219.exe
cd Disk1
unshield x data1.cab
cd INF_xp_File_Group
ls
```There is your .inf file, netwg311.INF.

Post back if you get stuck.

---

