---
title: "sudo: /etc/sudoers is mode 0640, should be 0440"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by 9000cse on 2011-06-23
Hi All that read this.
How to I change this?

> asjmm@asjmm-Saviour:~$ sudo /etc/init.d/samba stop
sudo: /etc/sudoers is mode 0640, should be 0440
sudo: no valid sudoers sources found, quitting
asjmm@asjmm-Saviour:~$ 


Thanks.
Andy

---

### Post by sisco311 on 2011-06-23
Hi,

Boot into *Recovery Mode* and change the file's permissions back to 0440. See: [http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by chili555 on 2011-06-23
I don't know for absolutely sure, but I'd try:```
sudo su
chmod 0440 /etc/sudoers
exit
```

---

### Post by 9000cse on 2011-06-23
Thanks Chilli, but that did not work.
I'll give Sisco a try.
Cheers Guys.

---

### Post by 9000cse on 2011-06-23
OK, so I have tried Chills example. Dame system did not want to reboot into UBUNTU 10 .
After trying the recovery side of things, Got nowhere. I have had to reinstall. So, lets do the 11 bit. 
This is fun...It did not fully install.  Opening another thread.    
Cheers Guys.

Hi all. OK, after a tip I was given to change sudo 
> 
sudo su chmod 0440 /etc/sudoers 
exit
My system said enough is enough and stopped booting, would not come up. BLACK screen.
I followed the recovery process, but still a no go.  I do think the system was unstable before the above code.
So, decided to upgrade to 11.04.  But that did not fully work either.  Somethings just not working. i.e. UBUNTU Software center. That star just  keeps spinning, around and around.  I left it for a time, went and had  dinner. so good 30 minutes, got back, and still she is turning.
So looked here and found this.

> 
sudo apt-get update
After it does what it does, lots of lines with you know what. It ends with


> 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
So, my first problem needs to be solved before I go to the next one.

Help needed guys, Please.

---

### Post by chili555 on 2011-06-23
> I do think the system was unstable before the above code.I think that's your issue, not the permissions of sudoers. It is simply a file; a list of who on the system is allowed to use 'sudo.' Even if the permissions were galaxy-wide, I believe it would simply reduce security and cough out a warning, as you saw.

I executed the commands I suggested above and nothing changed; it didn't change because the mode was 0440 before and after I did the command.> chili@LAPTOP60:~$ ls -al /etc | grep sudoers
[COLOR="Red"]-r--r-----[/COLOR]   1 root root     574 2011-04-15 11:54 sudoers
drwxr-xr-x   2 root root    4096 2011-06-12 11:25 sudoers.d
chili@LAPTOP60:~$ sudo su
[sudo] password for chili: 
root@LAPTOP60:/home/chili# chmod 0440 /etc/sudoers
root@LAPTOP60:/home/chili# exit
exit
chili@LAPTOP60:~$ ls -al /etc | grep sudoers
[COLOR="Red"]-r--r-----[/COLOR]   1 root root     574 2011-04-15 11:54 sudoers
drwxr-xr-x   2 root root    4096 2011-06-12 11:25 sudoers.d

---

### Post by e79 on 2011-06-23
> 
                                                 Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.                      From a Terminal prompt, copy paste all the commands one by one :

1. ```
cd ~
```2. ```
mkdir lists
```3. ```
cd  /var/lib/apt/lists
```4. ```
sudo cp -r *  /home/username/lists
```(**make sure to replace 'username' with your actual username**)
5. ```
sudo rm -r *
```([COLOR=Red]**Make sure that you still are in '/var/lib/apt/lists' before executing this command !**[/COLOR])
6. ```
sudo apt-get update && sudo apt-get dist-upgrade
```This will get rid of this error for sure.  Once the error go away and you can successfuly update and upgrade your system, you can safely delete the 'lists' folder in your home folder.  But to be honest if you keep getting strange errors, try to go with a full reinstall, maybe somehting during the upgrade borked your system.

hope this helps

---

### Post by 9000cse on 2011-06-24
Thanks e79, that is the biz. seems to be OK. Stable at least and USC now works.
Cheers Andy

Now **[COLOR=red][[/COLOR][COLOR=red]SOLVED][/COLOR]**

---

### Post by e79 on 2011-06-24
I'm glad we corrected the issue ! As for marking the Thread as [SOLVED], it should be done via the thread tools :D

Best Regards

e79

---

### Post by 9000cse on 2011-06-24
Yes, and thanks again. As for Solving.  Always wondered where that hid.
Thanks again.
Andy

---

