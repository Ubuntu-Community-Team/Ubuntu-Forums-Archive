---
title: "when gets the hardware address of network card determined"
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by go4unkwn on 2012-08-03
hello

i have trouble to get a bash script working. the bash script gets launched from rc.local.
and it should run only one time after a clonezilla image restore (when the pc gets booted for the first time after the image restore).

one part of the bash script is to read the hardware address using ifconfig:

[HTML]mac=$(/sbin/ifconfig | grep ^eth* | tr -s ' ' | cut -d' ' -f6 | tr "[a-z]" "[A-Z]")[/HTML]the problem is i always get en empty string, if the script is launched during the boot process (launched by rc.local). if i launch the script in a terminal (as user root) by myself, the variable ${mac} holds the hardware address (and isn't empty).

further in rc.local i tried to set:

[HTML]( sleep 60 && /run/bash/script )[/HTML]it didn't help either.

then i created in the script a while loop

[HTML]# create empty mac string
mac=""

while [ -z "${mac}" ]
do
        mac=$(/sbin/ifconfig | grep ^eth* | tr -s ' ' | cut -d' ' -f6 | tr "[a-z]" "[A-Z]")
        sleep 10

       ... some code ...

done
 [/HTML]it din't help either. in the task manager i see the script (with the  loop from above) is running all the time but the string in "${mac}" is  always an emtpy string.

then i can copy/paste the code

[HTML]mac=$(/sbin/ifconfig | grep ^eth* | tr -s ' ' | cut -d' ' -f6 | tr "[a-z]" "[A-Z]")[/HTML]into a terminal and execute it (while the script is still running and returns empty strings) an i get the hardware address extracted.

does anybody have an idea why the script returns empty strings?
is there another way to get the hardware address from an ethernet card?

kind regards, go4unkwn.

---

### Post by go4unkwn on 2012-08-07
Find a simple solution to my ifconfig problem (extract hardware address).

I replaced ifconfig with ethtool and everything works fine.:P

kind regards, go4unkwn

---

