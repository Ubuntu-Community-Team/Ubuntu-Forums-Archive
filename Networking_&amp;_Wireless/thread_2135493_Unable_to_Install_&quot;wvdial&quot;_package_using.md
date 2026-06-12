---
title: "Unable to Install &quot;wvdial&quot; package using apt-get install"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by kiran1247 on 2013-04-14
Hi,

I'm unable to install wvdial package using the following command in the terminal

$sudo apt-get install wvdial

It throws error message like : unable to install , because wvdial package doesn't exists.

How to install wvdial , and gnome-ppp and more packages if needed ?

I need to install wvdial , and started configuring reliance netconnect , & go with surfing.

Please do help me to resolve my issue.

Thanks in advance.
Kiran

---

### Post by prshah on 2013-04-14
> **kiran1247 said:**
> 
$sudo apt-get install wvdial

It throws error message like : unable to install , because wvdial package doesn't exists.


In a normal situation, this command should work fine. If it doesn't work for you, check:

a) Your header says you are using 10.10, which is EOL (End of Life). EOL releases do not have active repositories maintained anymore, and possibly this may one reason for your error.

b) If you are using a more recent release, ensure that your software repository information is updated (especially if this is a freh install). From the terminal (Dash-Terminal), run the command```
sudo apt-get update
``` this will create / refresh the list of software available in the repositories.

Please post back if you are still having trouble.

---

### Post by kiran1247 on 2013-04-15
Thanks PRShah for quick reply on my isssue.

There's no luck , still error!

I've tried executing the command like  -
 
sudo apt-get update ( but this doesn't executed successfully, because actually it was searching for packages/dependecies from internet which i don't have ,- so command fails)
( I guess necessary packages where NOT installed by default while installing Ubuntu)

Let me give brief background how I installed UBuntu :

1. Downloaded one fresh copy of UBuntu software from official UBuntu web-site itself ( downloaded latest ISO copy 12.04LTS)
2. I used my pendrive to make bootable drive.
3. Using pendrive I've installed UBuntu 12.04LTS on to my HP laptop successfully.

Now, I would like to use/configure my "reliance netconnect" usb device in UBuntu , and start surfing internet.

Please help me , what steps do I need to follow further to make internet work on UBuntu.

Thanks
Kiran

---

### Post by prshah on 2013-04-17
> **kiran1247 said:**
>  
sudo apt-get update ( but this doesn't executed successfully, because actually it was searching for packages/dependecies from internet which i don't have ,- so command fails)
( I guess necessary packages where NOT installed by default while installing Ubuntu)


Please quote the error message.

Do you not have wired or wireless (WiFi) Internet access? If you can (temporarily) use a wired or wireless connection, the above command should be able to complete successfully.

Failing all else, you can download wvdial for precise (12.04) from [http://packages.ubuntu.com/precise/wvdial](http://packages.ubuntu.com/precise/wvdial) however, this is not recommended, as there may be confusion as to dependency satisfaction. If you want to try anyway (can't harm anything), download the relevant package from the above link (note the saved location). Then, open a terminal (Dash-Terminal) and give the following commands```
cd ~/Downloads # replace ~/Downloads with the correct download location
sudo dpkg -i wvdial_1.61*
```

If you get any error messages, please post them verbatim, for further specific assistance.

---

