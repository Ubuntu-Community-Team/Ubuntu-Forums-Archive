---
title: "PPTP-Linux Install - Unmet Dependency"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by 1slorunner on 2006-06-07
To All --
I am trying to install the PPTP Client using the following command:
apt-get install pptp-linux 

and I am getting this error:

The following packages have unmet dependencies:
  pptpconfig: Depends: php-gtk-pcntl (>= 1.0.0) but it is not going to be installed
E: Broken packages
 
Can someone please advise on how to resolve this issue?  Thanks in advance.

1slorunner

---

### Post by engleb on 2006-06-10
I ran into this same issue.  I was able to get it installed by enabling the Universe repos, running a sudo apt-get update, then doing the sudo apt-get install pptpconfig.  libglade0 is in there and it is what php-gtk-pcntl was looking for when I tried to install it seperately.

I haven't configured it and tried it out yet, but I'm assuming it'll work.

**Update:** after installing this, I am unable to connect using pptpconfig, it appears to hang and errors out.  I haven't had much time to troubleshoot, if anyone else figures this out, please let me know.

---

### Post by Geoff2077 on 2006-07-28
Finally someone who knows what they are talking about. I have been trying for 10 days to find complete instruction on installing pptpconfig. Always the missing dependencies. The clue is to  add the Universe repos - thanks.

I then ran the pptpconfig from a root terminal. Fired right up with the gui interface.

we have MS small business server at work. I just entered the server details, eg.
company.dyndns.org
my user id: ghughes 
and my password : ****
Added this. Then highlighted and click start. Connected!! (shit really happens)

I then stopped the connection and went to routing tab, interface only (my files are on the server itself) and entered the ip address for the server:
192.168.16.2/24  - 24 gives a mask of 255.255.255.0, although I have no idea what this has for significance as it is not needed as input when setting up VPN with windows XP.

I added the route, then went back to server tab, selected the company and clicked on Start again. Once again connection.


Now a couple of questions please (note that I am complete newbie)...
1. how do I actually see the files on the vpn server. 

2. how do I create a menu item in ubuntu to start the pptpconfig gui. Having to run it from terminal each time seems silly.


Cheershttp://ubuntuforums.org/images/smilies/rolleyes.gif
Geoff

---

