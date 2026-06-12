---
title: "Connect To ISA VPN .."
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by eltech on 2006-06-28
Greetings,

I have just setup Ubuntu and bascially if i can VPN to work, i can use remote desktop and connect to our servers; i can stick with Ubuntu as my home desktop. That would make me happy.

I'm a Gentoo linux user for servers mainly, but with all the hacking in Gentoo; id like an easy linux desktop .. Ubuntu seems to be the one for the job :cool: 

But so many places to click here and there to get a VPN connection .. its a bit aggravating. All i need to do is connect from home to the job. We use ISA as our connection and it works 1-2-3 in windows. 

So i get to install pptpconfig and all the dependecies and run it through gui .. it wont save. it claims that it cant access the lock file. I am doing **sudo pptconfig**. I try to run it from command line: pptconfig it says **Fatal error: php-gtk: could not open display in /usr/bin/pptpconfig.php on line 31**

I also tried KVPNC and all that does is just **connecting**.. :-\" 

Anyone have any suggestions.. im wondering if pptpconfig will work if i can get by these odd little errors ... 

Any suggestions?

Thanks in advance.

Lenny

---

### Post by eltech on 2006-06-28
Ok ... so Gentoo definitely gave me one quality .. search search search .. ive eliminated the display error using this.. [http://ubuntuforums.org/showpost.php?p=963615&postcount=6](http://ubuntuforums.org/showpost.php?p=963615&postcount=6)

And i can connect! yay!

BUT :) ... seems nothing works using names.. i have to use the IP to access anything eventhough i see the DNS server placed in the resolv.conf file and i see it say it in the terminal ..

---

### Post by eltech on 2006-07-12
> **eltech said:**
> BUT :) ... seems nothing works using names.. i have to use the IP to access anything eventhough i see the DNS server placed in the resolv.conf file and i see it say it in the terminal ..bump .. any idea? :-k

---

### Post by mips on 2006-07-12
Check your DNS config.

---

### Post by eltech on 2006-07-12
> **mips said:**
> Check your DNS config.DNS config in the pptp cofig gui?

If so i have tried automatic and manually entering them

THink anything having to do with the fact that my eth0 is also manually configured? I cant see how seein that so many people would probably be using manual configured ip addresses.

Any help is appreciated.

;)

---

### Post by cmnorton on 2007-08-23
"So i get to install pptpconfig and all the dependecies and run it through gui .. it wont save. it claims that it cant access the lock file. I am doing sudo pptconfig. I try to run it from command line: pptconfig it says Fatal error: php-gtk: could not open display in /usr/bin/pptpconfig.php on line 31"

I am also getting this problem with 6.06 LTS. I have the 6.06 installed on a laptop and do not have this problem, and never had the X login problems I have read about. Any ideas?

Since posting this, I found that running gksu /usr/sbin/pptpconfig fixed the problem.

---

