---
title: "networking in a school with Ubuntu"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by delfick on 2006-07-07
hi

In my Cisco class in school we decided to install Ubuntu on one of the computers. That part worked great so now it is installed :D 

Our issue is that we cannot use apt-get. We can see the network and connect to the internet in firefox.

Noting that to use firefox, we must put in a username and password from the school server (for example mine) and then we can use the internet. I am thinking that apt-get needs to login into the school network, but i am unsure wether this is the actual problem or how to get it to log into the school network.

So can anyone help us?

(note that i am one of the students and we go on a holiday for the next two weeks so we won't have access to the computers over that time... though help will be very appreciated so that when we get back we can get it working quickly (hopefully anyway :D))

thnx

---

### Post by blackjack6.21.91 on 2006-07-07
After you have used firefox and have logged into the network, does your connection still not work?

---

### Post by delfick on 2006-07-07
using firefox doesn't fix it...

---

### Post by delfick on 2006-07-08
hmmm, another idea

is it possible to log straight into the school network at Ubuntu's login screen?

---

### Post by mips on 2006-07-08
Your school probably uses a proxy server to grant access to the internet. You will have to configure ubuntu to use the network via the proxy server.

Go to System->Preferences->Proxy settings

To get the proxy server settings (IP address & Ports) you need to look at one of the existing windows machines or ask the network admin.

You can also configure firefox independantly with the proxy settings which will allow browsing but only browsing will work.

---

### Post by delfick on 2006-07-08
k then, i'll try that when we go back to school

thnx

---

### Post by delfick on 2006-07-08
actually, i just looked at it and i remember we had already setup the proxy settings...

any other ideas?

(sry for double posting)

---

### Post by mips on 2006-07-09
Just double check and make sure all the settings are correct, you also need to specify the username & password. 'Automatic' proxy settings don't usually work just incase, someone else had that problem a short while back.

---

### Post by delfick on 2006-07-09
k, thnx

I'll tell if it works when we get back...

(don't hold ur breath...:D)

---

### Post by delfick on 2006-07-25
ok then...back at school :'(

tried setting the proxy settings correctly...and it doesn't seem to be working...as before i can get firefox to work 

But i go into the terminal and do a "sudo apt-get update" and for all the repositories i get something like this 

> Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/Release.gpg](http://www.beerorkid.com/compiz/dists/dapper/Release.gpg)  Could not connect to CURRIC4055.INTERNAL:8080 (10.59.104.130). - connect (111 Connection refused)


anymore ideas?

---

### Post by mips on 2006-07-25
Does the proxy server allow all ports or only certain ones ? Check with the admin.

---

### Post by delfick on 2006-07-25
k then...will do that next time i have cisco which is in a couple of days...

---

### Post by Braino on 2006-07-25
I have a problem similar to this when I install Ubuntu at home; the internet works and everything, but apt can't connect. I usually fix this by editing /etc/apt/apt.conf and removing the line (usually the only line there) that mentions proxies. 

I don't have a proxy, so you might not want to remove this line; but it could be the source of your problems.

-Braino

---

### Post by delfick on 2006-07-26
> **Braino said:**
> I have a problem similar to this when I install Ubuntu at home; the internet works and everything, but apt can't connect. I usually fix this by editing /etc/apt/apt.conf and removing the line (usually the only line there) that mentions proxies. 

I don't have a proxy, so you might not want to remove this line; but it could be the source of your problems.

-Braino

thnx, when i next have cisco (which i just realised is in two days from today  (instead of tommorrow as i said in my last post) due to how this week is) i shall try to do that as well...

---

### Post by delfick on 2006-07-28
k then....

removing the line about the proxy didn't fix it :'(

then i tried using a "autoconfiguration url"

then it comes up with a new error..... 407 ...something about the isa server didn't authenticate or something about denieing (forgot to post the error in whilst i was still at school :( )

so at school...i tried to get the technician dude to help but he wasn't there.....

so i'll try again after the weekend :D

---

### Post by Braino on 2006-07-28
No no, don't remove it. If you have a proxy, you will probably need to configure it with that line. 
It should look something like this:
```

Acquire::http::Proxy "http://user:pwd@proxy:port";

```

From some reading, it seems that if you setup the proxy in System->Preferences->Network, it overrides what you put in apt.conf, and apparently doesn't allow authentication. So, if you setup apt.conf to use proxies, don't set it up in the network preferences. 

Arnieboy might be able to help you:
[http://ubuntuforums.org/showpost.php?p=541276&postcount=1006](http://ubuntuforums.org/showpost.php?p=541276&postcount=1006)

---

### Post by delfick on 2006-07-28
thnx...that looks very promising :D

---

### Post by delfick on 2006-08-04
ok....got the technician to try and help me today....and SUCCESS apt-get can now contact the internet.....

though there is a drawback but it's all good....

basically to get it to work we set it to have a static IP address...
then set the server so that internet access to this machine was before any protocols (or something like that...not too sure what he did :p)

so now it can access the internet....though because we can't define what user on the network is using the machine, this way creates a security risk so basically everytime i want to use the computer i have to go to the technician and ask for the interent access to the machine to be enabled again....

This isn't a problem because playing around with linux isn't important in the whole scope of things......


anyway...thankyou all for ur help....:D

---

### Post by delfick on 2006-08-05
(excuse the double post)

after thinking about it.....

When use windows on a setup such as in a school where u log straight into the school network....

is it possible to do the same with Ubuntu...?
that way i wouldn't log into the local machine, but instead into the network under my username....

?????

---

### Post by mips on 2006-08-05
> **delfick said:**
> (excuse the double post)

after thinking about it.....

When use windows on a setup such as in a school where u log straight into the school network....

is it possible to do the same with Ubuntu...?
that way i wouldn't log into the local machine, but instead into the network under my username....

?????

Their proxy is probably linked to microsoft network authentication system. If I recall correctly I think it is possible to do in linux. Start searching for logon MS network or something of the sorts.

---

### Post by delfick on 2006-08-05
> **mips said:**
>  Start searching for logon MS network or something of the sorts.

will do...thnx

---

### Post by delfick on 2006-08-07
> **delfick said:**
> will do...thnx

excuse my noobness, but i can't find anything that looks like it's gonna help me...:'(

are u able to help me further...?

thnx

---

