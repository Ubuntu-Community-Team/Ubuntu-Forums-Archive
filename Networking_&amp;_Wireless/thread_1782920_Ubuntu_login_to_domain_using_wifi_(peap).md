---
title: "Ubuntu login to domain using wifi (peap)"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by kriss3d on 2011-06-15
I know ive posted this question a while ago but considering nobody answered i might have stated my questions in a wrong way. Here goes.

Im having Ubuntu 9.10 on serveral laptops (netbooks actually) connected to domain. 
This means that every person wanting to use the computer needs to log in and get the credencials from the AD server (Windows server)

This all works just fine. They can log in and all that jazz.

However this does NOT work with wireless which is the point of having a laptop in the first place.
Since you need the user credencials (name and password) in order to login to the wifi.
This is solved somhow in Windows where it will use your password and username and see if that allows you to connect to the wireless. After that it verifies you against the Server AD.

How do i make ubuntu attempt to connect to the wireless while logging in so the user gets verified ?
If i set a static user and password in the network manager and lets everybody uses that it works just fine. But then the server crew wouldnt know who does what once logged in. Plus they wouldnt get their own windows shares and such..

I cant belive im the only one who has a need to login to linux using wifi for authentication.. How is this solved ?

---

### Post by dandnsmith on 2011-06-15
You're not the only one - it usually pops up with users of a university network or similar.

I've never had the immediate need to solve it, but would start with the man pages for 'wireless' and 'ifwconfig' and think about a suitable script which would automate the process for you.

Just seen what might be the start for you in [this posting](http://ubuntuforums.org/showthread.php?t=976151)

Good Luck

---

### Post by kriss3d on 2011-06-15
So there isnt a solution to this ??
In crying on the inside already and i REALLY dont want to have to resort to Windows to solve this problem. Somhow Microsoft solved this in a rather beautyful way.
Every guide i find resgarding getting a wireless connection before login always uses some puny script with a static username and password.
Every user has to supply a username and a password to get access to the wifi. But since you cant get logged in before you are connected to the wifi (due to you also have to be authenticated against a AD server) its a problem..

---

### Post by dandnsmith on 2011-06-15
There may be a solution, which, however, I don't yet know of.
You're comparing with a setup which hs M'soft soft at both ends - and so they make sure the solution (for them) is 'beautiful' (not unexpectedly).
I'm sure that any solution with a script can be crafted to accept the username and password in a different manner (obtain it from the ubuntu password file ...) and make life easier for the end user, it just so happens that the linux/ubuntu effort has gone to solving the most frequent problem (people accessing wifi as they move around) - as has the Windows equivalent - but the other bit is much more localised, and hasn't been provided as a 'standard' solution.

---

### Post by kriss3d on 2011-06-17
I just thought of somthing.. Is it possible to have a post login script which connects to a PEAP network using the users login name and password ?
Naturally the password should be read from enviormental variable and not directly each time. 

Since we have a open network - unencrypted which should also allow for AD authentication i thought about having the network automaticly connect to this network first.. Which doesnt requires any login info. Then the user logs in and gets verified in the AD. After login a script switches network to the peap one while using the users credentials to sign on.

Does this seem feasable ?

---

### Post by dandnsmith on 2011-06-17
Seems worth a try.

Good Luck

---

