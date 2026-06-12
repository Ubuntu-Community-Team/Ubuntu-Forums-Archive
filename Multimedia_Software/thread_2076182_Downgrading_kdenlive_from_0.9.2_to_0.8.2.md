---
title: "Downgrading kdenlive from 0.9.2 to 0.8.2"
date: 2012-10-25
forum: Multimedia Software
---

### Post by TomShootsPhoto on 2012-10-25
Hi!

SO I recently updated Kdenlive to 0.9.2, but there are some features I do not like. I would like to downgrade to 0.8.2, if possible. 

Is there any way to do this? :confused:

Thank you!

---

### Post by shantiq on 2012-10-25
```
sudo apt-get remove --purge kdenlive
```


then install [**this deb**]("http://archive.ubuntu.com/ubuntu/pool/universe/k/kdenlive/kdenlive_0.8.2.1-1ubuntu1_amd64.deb")   if you have 64    or if [**32 **]("http://archive.ubuntu.com/ubuntu/pool/universe/k/kdenlive/kdenlive_0.8.2.1-1ubuntu1_i386.deb") 


then  lock it in your synaptic   package/lock version


==================


actually there is an even quicker route   [if 8.2 still there]

go to synaptic   highlight kdenlive/package/force version/pick 8.2/force version/apply

then lock as above

---

### Post by TomShootsPhoto on 2012-10-25
Neither of these solutions work. 

The first one just gives me an error and the second one just uninstalls kdenlive. 

Any other tips?

---

### Post by shantiq on 2012-10-25
Please how about first we say thank you   then  "Neither of these solutions work FOR ME as yet"

what did not work?  explain yourself.   what did you actually do?    please explain step by step

the 2 methods explained are right     you  possibly misunderstood something

---

### Post by TomShootsPhoto on 2012-10-25
Sorry, I should've given enough info.


So when I try to do the first thing, it gives me this: 
[IMG]http://i.imgur.com/YMffS.png[/IMG]


Then I tried your second method, and it all went fine until I pressed apply: 

[IMG]http://i.imgur.com/ridIb.png[/IMG]

Then I tried manually removing the dbg package, and tried again. 

This time, it was completely removed:

[IMG]http://i.imgur.com/dsTSV.png[/IMG]

What do I do?

---

### Post by TomShootsPhoto on 2012-10-25
Bump

---

### Post by shantiq on 2012-10-25
ok i see  
you have broken packages

so let us  remove everything again to make sure and start with method 2

so in terminal ```
sudo apt-get remove --purge kdenlive
```  if it tells you nothing installed no sweat


then open synaptic


enter kdenlive  highlight/ package/force version/pick 8.2/apply


then it will tell you again that you have broken packages


so then **2 options**

1.

click on edit/fix broken packages/apply

and that should do it and install your 8.2 with correct dependencies


2.   or shut synaptic   open terminal   and    > sudo apt-get -f install    will also fix broken packages so one or the other your choice






and if all ok then lock package  [again from synaptic]



see how that goes:KS

---

### Post by TomShootsPhoto on 2012-10-25
Well, not so much better... 
 
I made this video to show what happens. 

[http://www.youtube.com/watch?v=QRcV-7rdMIU]("http://www.youtube.com/watch?v=QRcV-7rdMIU")

Thank you for your help, but I think I'll have to reinstall the whole OS now... I've must've messed up something really badly

---

### Post by shantiq on 2012-10-25
no need to reinstall OS    nothing is damaged   no worries


you still have 9.2 installed in your video  so first remove it

```
sudo apt-get remove --purge kdenlive
```

then check in your synaptic that it is **unticked**


once u know it is gone shut synaptic and run this in terminal

---

### Post by TomShootsPhoto on 2012-10-25
Hm... It seems to give me a 404 error. :(

> tvass@Nimbus:~$ wget [http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb) && \
> sudo dpkg -i kdenlive_0.8.2.1-1ubuntu1_amd64.deb
--2012-10-25 21:25:04--  [http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb)
Resolving archive.ubuntu.com (archive.ubuntu.com)... 91.189.92.201, 91.189.92.202, 91.189.92.156, ...
Connecting to archive.ubuntu.com (archive.ubuntu.com)|91.189.92.201|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-10-25 21:25:05 ERROR 404: Not Found.


---

### Post by shantiq on 2012-10-25
-------------------

---

### Post by shantiq on 2012-10-25
haaaaaaaaaa  sorry   the damn quotes contacted the address


so click [here ]("http://archive.ubuntu.com/ubuntu/pool/universe/k/kdenlive/kdenlive_0.8.2.1-1ubuntu1_amd64.deb")    you are on 64 are you not and save to home folder


then  

> sudo dpkg -i kdenlive_0.8.2.1-1ubuntu1_amd64.deb 

 
and if it tells you broken packages run

>  sudo apt-get -f install 
 
 then should be fine

---

