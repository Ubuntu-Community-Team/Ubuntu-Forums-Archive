---
title: "SMBFS screwing me?"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by DetergentCandy on 2009-12-28
Okay, so I was trying to get my Ubuntu laptop, on the same fileshare network as my mother's Windows XP box. I wasn't totally sure what to do, and read in a thread here that you have to us Samba, as well as smbfs. 
I already had Samba(Ubuntu 9.1 comes with it?), so I grabbed smbfs through Synaptic.

Well, now I don't have internet :D
I'm connected to eth0, but...I can't get online.
I get a message in my task bar at the top that says:
"The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by clicking on this icon and then selecting 'check for updates' and check if some of the listed repositories fail."

Right, but how do I update without internet?

Did I do something wrong when I installed smbfs?

What the heck did I do?

---

### Post by headvampyre@hotmail.co.uk on 2009-12-28
Hi it shouldn't be anything to do with samba and if saying repositories may be out of date go to

applications -> accessories -> terminal 

and type

ifconfig

if it comes up with something like xxx.xxx.x.x on eth0 or wlan0 you are connected to router (x will be a number) then continue if no post back

sudo apt-get upgrade

which will upgrade your repositories then update your repositories

system -> administration -> update manager 

once update manager is open click check then install all the updates. once you have rebooted go to 
Places -> Network -> Windows Network Then the name of your mums workgroup / domain then click on the computer / server name

---

### Post by DetergentCandy on 2009-12-28
That's the thing. I can't get online. So how do I check for updates?

"An error occured.
W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg) Could not resolve 'us.archive.ubuntu.com'."

That is one of like, a dozen similar messeges I get when trying to update.

I am connected to router, according to ifconfig. 

Also, when I click on Windows Network, I just get an error messege.
"Unable to mount location. Failed to retrieve list from server."

I am so confused :P

---

### Post by headvampyre@hotmail.co.uk on 2009-12-28
have you changed any proxy settings as this can interfere with stuff if not look for solutions on net but i never looked cos i run important domain so i just backup and reinstall which fixes probs which i done in 50 mins so it wont take 2 long to reinstall.hope you fix prob coz it gets annoyin

---

### Post by anagor on 2009-12-28
It's possible that there is a DNS configuration error somewhere.
You can override it in NetworkManager.
Right click on the NM icon -> edit connections -> choose either the eth0 or wlan if you use wireless, the click on edit -> IPv4 Settings tab -> choose "Automatic DHCP adress only" this will allow you to insert the dns servers addresses manually. you can use google's dns which are 8.8.8.8 and 8.8.4.4
Maybe this will help with getting the updates.

As for the "Unable to mount location. Failed to retrieve list from server." error, I've seen it on networks with windows XP. the best remedy from what I recall is, after you install smbfs, make one folder in your ubuntu shared, so that windows will see it. from this point on, both machines will probably see each other.

---

### Post by headvampyre@hotmail.co.uk on 2009-12-28
actually i forgot about dns but could you connect to internet b4 installing smbfs and also playing around with dns will mess up your internet so try and find your router dns settings and use them for dns on the internet connection or disable networking and re-enable it with 

sudo /etc/init.d/networking restart in terminal 

that might reset all the settings

also try

ifdown -a

then

ifup -a

---

### Post by DetergentCandy on 2009-12-28
Uh...problem solved :P

Thanks for all the input.

Moved my laptop into another room, plugged it into that internet connection, and it worked 0.o Installed updates, hooked it back up to the router in my room, and it works o.0

Awesome. I love technology xP

---

