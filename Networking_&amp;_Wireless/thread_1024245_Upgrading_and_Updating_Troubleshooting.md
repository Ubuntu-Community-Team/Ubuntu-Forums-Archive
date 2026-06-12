---
title: "Upgrading and Updating Troubleshooting"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by James Yaeger on 2008-12-28
Hello Everyone

Today I used a disk that my brother made for me to install Ubuntu 6 on my desktop. I got it and it runs. The problem is whenever i try to install a program or upgrade to Ubuntu 8.10, i get an error message. 

"Could Not Download All Repository Indexes"

Then it goes into a thing describing how i might have network problems. 
Then it shows a list of websites. this is a copy of one list:
> [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]

What does that mean and how can I fix it?:confused:

---

### Post by 67GTA on 2008-12-29
If you are talking about Gutsy 6.10, it is dead. It only had 18 months of support. You could try updating to Hardy which is good for a couple of more years. Open a terminal and run ```
sudo gedit /etc/apt/sources.list
``` Then find each instance of gutsy and replace it with hardy, save it, and try again.

---

### Post by tmrotz on 2008-12-29
I am having a similar problem and have looked all over the internet for a solution to ANY "Could not download all repository indexes." I was unsuccessful.

There must be a way to analyze and fix this problem no matter what system your running.

My system and error:
Ubuntu 8.04.1 _Hardy Heron_ - Release i386 / hardy main restricted

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.gz](http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.gz)  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cariboo on 2008-12-29
If you are having a problem updating the repositories, try another server. To do this go to System-->Administration-->Software Sources click the download from dropdown and select Other. Next click Select Best Server and let it check to see which is the fastest, when it is done if you want the sever that the program came up with click Choose server.

The program will want to update, and once it is done you should be able to do updates and install packages.

Jim

---

### Post by Partyboi2 on 2008-12-30
> **tmrotz said:**
> I am having a similar problem and have looked all over the internet for a solution to ANY "Could not download all repository indexes." I was unsuccessful.

There must be a way to analyze and fix this problem no matter what system your running.

My system and error:
Ubuntu 8.04.1 _Hardy Heron_ - Release i386 / hardy main restricted

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.gz](http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.gz)  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.
looks like you have a edgy repo in your sources.list can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list
```

---

### Post by Toneh on 2008-12-30
I have a problem upgrading. I have ubuntu 8.04 LTS an a netbook, which has no cd-rom drive, so I have to update from the update manager.
When i try to update, it says:
ailed to fetch [http://mirror.imbrandon.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

So i cant upgrade... Would you guys help me out please?

---

### Post by TonyBenson on 2009-01-16
same problem here

any one got a clue?

---

### Post by Partyboi2 on 2009-01-17
As mentioned earlier in this thread have you tried changing your download server in Software Sources (System>Admin>Software Sources>1st tab)

---

### Post by amitaigolub on 2009-03-24
Hey, I'm having the same problem and also a noob to ubuntu,

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]

I have tried changing the server according to the previous recommendations but that didn't really help. I thought I'd have a look at the site itself so I looked here:

[http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) 

but there seems to be no edgy there. I'm also running 8.10, so shouldn't I just change this update to the same http only instead of edgy, there should be intrepid? if so how do I do that?

thanks for the help sorry if the whole preamble was a bit much :)

---

### Post by Partyboi2 on 2009-03-25
> **amitaigolub said:**
> Hey, I'm having the same problem and also a noob to ubuntu,

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]

I have tried changing the server according to the previous recommendations but that didn't really help. I thought I'd have a look at the site itself so I looked here:

[http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) 

but there seems to be no edgy there. I'm also running 8.10, so shouldn't I just change this update to the same http only instead of edgy, there should be intrepid? if so how do I do that?

thanks for the help sorry if the whole preamble was a bit much :)
To make changes you can open a terminal (Applications>Accessories>Terminal) and open your sources.list with gedit
```
gksu gedit /etc/apt/sources.list
```
then look for the edgy entry and check that there is not a intrepid entry all ready for that repo. If there is then you can delete the edgy repo as you can not have duplicate entries. If there is no intrepid entry for the same repo then you can replace 'edgy' with 'intrepid'
Then save the changes and close gedit then back in the terminal
```
sudo apt-get update
```

---

