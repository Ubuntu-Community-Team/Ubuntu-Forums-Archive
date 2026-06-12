---
title: "MAC swap"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Hawaiisnowstorm on 2009-12-06
Okay, this is gona a few questions in it.
I wrote a shell script that scrambles the last 3 sets of numbers in a mac address when its told to run - I had some free time and thought why not.  Currently it swaps the address with eth0 and runs when I click on it to run.  

```
#!/bin/bash
ifconfig eth0 down
MA=`ifconfig | grep HWaddr | cut -f 11- -d " " | cut -f -3 -d :`
NumberGen()
{
number=$[($RANDOM % 15 )] 
case $number in
	10 )
		XF=A;;
	11)
		XF=B;;
	12)
		XF=C;;
	13)
		XF=D;;
	14)
		XF=E;;
	15)
		XF=F;;
	*)
		XF=$number
esac
return
}
NumberGen ; A1=$XF
sleep 1;
NumberGen ; A2=$XF
sleep 1;
NumberGen ; B1=$XF
sleep 1;
NumberGen ; B2=$XF
sleep 1;
NumberGen ; C1=$XF
sleep 1;
NumberGen ; C2=$XF

ifconfig eth0 hw ether 
echo $MA:$A1$A2\:$B1$B2\:$C1$C2
ifconfig eth0 up

```

How would I tell it to edit to pull the current eth that is running to scramble it, and/or how would I tell it to run at start up and change the mac address on all eths before the nic is turned on

Thanks!:D

---

### Post by Hawaiisnowstorm on 2009-12-07
bump bump .. any one?

---

