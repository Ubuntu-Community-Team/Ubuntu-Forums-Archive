---
title: "Ubuntu 10.10 Refuses to connect to facebook"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by Stewie2kill on 2011-01-25
Hi guys,

     I recently removed Windows from a family member's laptop (Gateway NV52) and installed Ubuntu on it. I started out with Ubuntu 10.04 since it was an LTS. She's been very happy with it until a few days ago when it started acting up and refused to load almost any site she frequently visited. I decided to back up her data and do a fresh install of Ubuntu 10.10 (64bit) which is what I use. It installed fine, wireless works seamlessly as well. 

     However, Facebook refuses to load on any web browser (chrome, firefox, minefield, midori, etc.). It's only Facebook as well. The login page will appear but it will absolutely not login. I've tried it with several different accounts and it just flat out refuses. Every other site loads fine and fast, and logs in fine, but facebook just doesn't seem to load.

     I really do not want to have to move her back to windows 7 as she's prone to viruses and Ubuntu is just flat out awesome at virtually everything, but for her, social networking is her primary way of connecting to friends and it's critical for her to have access to that site. It's really her make or break feature, and if Ubuntu can't do it then she doesn't want anything to do with it. 

     I've looked everywhere for a solution to this. I've tried changing DNS servers, disabling and re-enabling the wifi, clearing the cache and cookies, even down to resetting the router we use, all to no avail. The site loads fine on every other PC regardless of the OS, and I've run out of places to look.

     My experience with the Ubuntu community has been top notch so far, and I'm not shy of any terminal work that may be needed, nor am I shy of fiddling with anything. I'm very comfortable in Ubuntu so if you've got any ideas, please fire away.

---

### Post by ivanovnegro on 2011-01-25
Hi,

strange. Is there anything regarding the firewall? The facebook site isnt blocked, that comes in mind but if you say with Windows its working. Take a look in the options of Firefox or the other browsers if there is something.

---

### Post by Stewie2kill on 2011-01-25
No, we have no firewall for that exact reason (risky I know, but I keep a close eye on our networking).

Interestingly enough, in Minefield (one of the nightly builds of firefox) I it just started loading and logging in. I'm not sure which one of the things I did that worked (or how long it will work). 

I did enable IPv6 under the wifi connection and set it to 'Automatic, addresses only' and left the DNS servers field blank and checked 'Require IPV6 addressing..." box. Before that I also re-ran bleach bit on firefox, and removed the secondary DNS server I was using so now it only has one for IPv4.

Now it works under minefield, but Chrome still refuses to load it as it has done basically through the whole run of this bit.

I'll try Chromium and report back if it also has the same issue. Maybe the open source bits of chromium actually work better on Ubuntu (would make sense).

(EDIT: Just got back from testing out chromium. It works on Chromium but not Chrome. Strange stuff. I wonder what is about Chrome that causes Facebook to flat out refuse connections. Chromium is basically the same thing though and that's her favorite so for now all looks good. Should this come up again I'll come back to this thread and update it, although hopefully I won't have to. This whole weeks becoming a networking a nightmare for me as Netflix is also refusing to connect on any of my netflix ready devices.

Thanks for responding. I'll mark this as solved for now and reopen it if it continues having issues.)

---

### Post by micajah on 2011-02-08
Please help. I am in the same situation as you, but I can't even get Facebook working in Chromium. Have you had any luck with the other browsers. I get nothing. I can get to the Facebook page, but I can't get past the login.

---

### Post by espressobeanie on 2011-02-08
Do you have java installed? Facebook requires javascript and by default Java is not installed. To install it, open your "Synaptic Manager" and click on Settings and Repositories. Click "Other Software" and then checkbox "Canonical Partners" and "Canonical Partners Source". Reload. Type java jre in the search box. Install the "sun-java6-jre" and "sun-java6-plugin". Then retry.  It should work on Chrome regardless. Mmmm... if it's all the browsers, then it sounds more like a firewall or filter problem. Type "sudo ufw status" and tell me what it says. Also, disable any addons or moblock if you installed them.

---

### Post by micajah on 2011-02-15
@espressobeanie I have done what you have suggested and still nothing. This is so frustrating, nothing is working. I have even done a clean re-install of Ubuntu. Any more suggestions?

---

### Post by micajah on 2011-02-15
@espressobeanie

sudo ufw status 
Status: inactive


?????

---

### Post by PaulReaver on 2011-02-15
first things first turn that firewall on **_[COLOR="Red"]now[/COLOR]_**... sudo ufw enable... if for some filesharing issue you need to turn it off... obviously its "sudo ufw disable"

check to see someone hasn't been messing with adblock or noscript... also check to make sure that facebook.com _isn't_ in the /etc/hosts file.


apart from this i can only advise you check the firewall on the router.

---

### Post by micajah on 2011-02-16
@PaulReaver I appreciate your help

How do I go about getting to and editing the /etc/host file. I did a quick search and did not find anything that made a whole lot of sense to me.

---

### Post by PaulReaver on 2011-02-16
to edit them you can open them with sudo
sudo gedit /etc/hosts

if you see something like

facebook.com       127.0.0.1

change it to 

#facebook.com      127.0.0.1


although if you've never done this before,..... it more than probably isn't the hosts file...


hope it helps....

---

### Post by besneatte on 2011-06-10
> **espressobeanie said:**
> Do you have java installed? Facebook requires javascript and by default Java is not installed. To install it, open your "Synaptic Manager" and click on Settings and Repositories. Click "Other Software" and then checkbox "Canonical Partners" and "Canonical Partners Source". Reload. Type java jre in the search box. Install the "sun-java6-jre" and "sun-java6-plugin". Then retry.  It should work on Chrome regardless. Mmmm... if it's all the browsers, then it sounds more like a firewall or filter problem. Type "sudo ufw status" and tell me what it says. Also, disable any addons or moblock if you installed them.

Are you joking? Java and Javascript are two separate technologies and this is definitely NOT the answer. 

[http://www.sislands.com/coin70/week1/javajs.htm]("http://www.sislands.com/coin70/week1/javajs.htm")

---

### Post by berryshar on 2011-08-13
I have a similar problem and so I downloaded the java and javascripts but nothing helped. When I type in facebook.com and press enter my loading sign comes on, I waited for 13 minutes and all my other websites works fine. I go back to windows 7 because of this and I really would like to fix it because i love ubuntu... please help me

---

