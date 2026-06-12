---
title: "Disabling ipv6 not successful."
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by rudra on 2006-07-05
Following some suggestions, I wanted to [COLOR="Red"]disable ipV6[/COLOR] by editing /etc/modprobe.d/aliases file. I added following  lines in this file and commented out the original entry "alias net-pf-10 [COLOR="Red"]ipv6[/COLOR]":

alias net-pf-10 [COLOR="Red"]ipv6[/COLOR] off
alias net-pf-10 off 
alias [COLOR="Red"]ipv6[/COLOR] off

But I still get the [COLOR="Red"]ipv6[/COLOR] entry in System -> Administration -> Network Tools after reboot. It seems [COLOR="Red"]ipv6[/COLOR] has not been disabled. What wrong am I doing?[COLOR="Red"][COLOR="Red"][/COLOR][/COLOR]

---

### Post by fragos on 2006-07-05
I did something similar but not the same that worked for me.  I created /etc/modprobe.d/bad_list with a single line "alias net-pf-10 off".  Like many Linux users I'm flying blind and following orders in this area.  The way that I used did work for me.  There seems to be some sensitivity as to where alias commands are placed.  Note System-> Administration-> Network Settings-> Hosts tab shows IPV6 connectivity even if its not being used.  There is no need but you can delete all the IPV6 Aliases.  If you enter "route" at the command line you shouldn't see any IPV6 addresses.  This gives the same results as System-> Administration-> Network Tools-> Netstat tab.  You didn't tell us which tab you were looking at.

---

### Post by GamerGarrett on 2006-07-05
I've tried editing the file aliases, and also adding the bad_list file.  Neither method has allowed me to get updates yet.  However, when I disabled ipv6 in Firefox, I was able to start browsing the web finally.
In Firefox:
clear address bar
type "about:config"
type in ipv in filter window
find Network.dns.disableIPv6 default boolean false
double click to change it to true

After that I could browse the web OK.
Anyone have any suggestions on how to get updates for me?

---

