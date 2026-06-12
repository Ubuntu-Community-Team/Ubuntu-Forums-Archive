---
title: "Download Videos from Youtube"
date: 2011-03-09
forum: Multimedia Software
---

### Post by amir786_z on 2011-03-09
hi there guys i was wondering, how can i download videos from youtube on ubuntu? can anyone suggest any software? thanks

---

### Post by babarosa on 2011-03-09
Hi,

you can use xVideoServiceThief 2.4.1-1~getdeb6 from here:
[http://www.getdeb.net/updates/ubuntu/10.04/](http://www.getdeb.net/updates/ubuntu/10.04/)

Greetings to Pakistan,
Michael

---

### Post by amir786_z on 2011-03-10
thanks :)

but when I click the install button ubuntu software centre appears with the error 

Not Found
There is not a software package called "Xvst" in your current software sources.

can u please tell me how to download this software. iam new to ubuntu.

---

### Post by johntaylor1887 on 2011-03-10
I use a Firefox add-on called Video DownloadHelper. It will even convert the video to any format you want. Great little app.

---

### Post by amir786_z on 2011-03-10
> **johntaylor1887 said:**
> I use a Firefox add-on called Video DownloadHelper. It will even convert the video to any format you want. Great little app.

thank u..:)

can u tell me how can i download softwares from [http://www.getdeb.net]("http://www.getdeb.net/"), i dont know how to download from this site. whenever i download something from this site error appears

Not Found
There is not a software package called "____" in your current software sources. there are many cool softwares on this site that i am unable to download:(

---

### Post by johntaylor1887 on 2011-03-10
Did you follow [this]("http://www.getdeb.net/updates/Ubuntu/10.10#how_to_install") how-to?

---

### Post by amir786_z on 2011-03-10
> **johntaylor1887 said:**
> Did you follow [this]("http://www.getdeb.net/updates/Ubuntu/10.10#how_to_install") how-to?

i hav followed the step 1 and installed getdeb-repository_0.1-1~getdeb1_all. but still cant download [xVideoServiceThief]("http://www.getdeb.net/software/xVideoServiceThief") or any other software. iam using ubuntu 10.10. i think i need ~getdeb6 for 10.10?

---

### Post by johntaylor1887 on 2011-03-10
What happens after you click install?

---

### Post by amir786_z on 2011-03-10
> **johntaylor1887 said:**
> What happens after you click install?

Not Found
There is not a software package called "____" in your current software sources.

Every software that i install same error appears.

---

### Post by johntaylor1887 on 2011-03-10
OK. I havn't used getdeb for a long time, but I just did step 2 of the how-to for getdeb, (manual install of the repo) and worked perfectly. But the only thing is, there is no longer software sources choice in administration. Open up synaptic package manager and go to **settings**>**repositories**>**other software** (tab)> **+add** button and put in:  

**deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb apps**

close window and reload when asked. Close synaptic. Then open a terminal and do:
```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```
then
```
sudo apt-get update
```
You should now be able to download from getdeb.net

---

### Post by amir786_z on 2011-03-10
> **johntaylor1887 said:**
> OK. I havn't used getdeb for a long time, but I just did step 2 of the how-to for getdeb, (manual install of the repo) and worked perfectly. But the only thing is, there is no longer software sources choice in administration. Open up synaptic package manager and go to **settings**>**repositories**>**other software** (tab)> **+add** button and put in:  

**deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb apps**

close window and reload when asked. Close synaptic. Then open a termial and do:
```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```then
```
sudo apt-get update
```You should now be able to download from getdeb.net

thanks man ....:D:D:D
u r awesome :D

---

### Post by johntaylor1887 on 2011-03-10
Glad you are happy now, enjoy.

---

### Post by beew on 2011-03-10
It is called xvst in Synaptic. If you have enabled the getdeb repo you should be able to find it there after you reload Synaptic (or go to terminal and type
```
sudo apt-get update  
sudo apt-get install xvst
```

But I prefer the firefox plugin VideoDownloadHelper

---

### Post by johntaylor1887 on 2011-03-10
> **beew said:**
> It is called xvst in Synaptic. If you have enabled the getdeb repo you should be able to find it there after you reload Synaptic (or go to terminal and type
```
sudo apt-get update  
sudo apt-get install xvst
```

But I prefer the firefox plugin VideoDownloadHelper

Well, that's the whole thing, we had to get the getdeb repo installed first, which obviously didn't work for the OP the first time around. Hence, the suggestion to install it manually. Of course, it will show up in synaptic after the repo is properly installed.

But the main this is, we have another satisfied customer. ;)

And yeah, I agree about video downloadhelper. It's the best I've used so far.

---

### Post by amir786_z on 2011-03-10
> **beew said:**
> It is called xvst in Synaptic. If you have enabled the getdeb repo you should be able to find it there after you reload Synaptic (or go to terminal and type
```
sudo apt-get update  
sudo apt-get install xvst
```But I prefer the firefox plugin VideoDownloadHelper

thanks:D  i will also try VideoDownloadHelper..:D

---

### Post by amir786_z on 2011-03-10
Ubuntu rockssss :D:):D

---

