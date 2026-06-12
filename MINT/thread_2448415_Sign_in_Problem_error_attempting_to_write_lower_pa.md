---
title: "Sign in Problem: error attempting to write lower page; rc = [r-28]"
date: 2020-08-07
forum: MINT
---

### Post by user-mane on 2020-08-07
Hi All,

So, have been on my laptop (Linux Mint 20 on Alienware r4 17) today and I noticed that I  was unable to open any other programs other that my browser (firefox). I  figured that I would just restart the machine to resolve this but upon  entering the password I get the following four lines displayed before  taking me back to the login screen:

 "[       16.822139] encryptfs_encrypt_page: Error attempting to write lower page; rc = [r-28]"
 "[       16.822195] encryptfs_encrypt_page: Error attempting to write lower page; rc = [r-28]"
 "[       16.822236] encryptfs_encrypt_page: Error attempting to write lower page; rc = [r-28]"
 "[       16.822284] encryptfs_encrypt_page: Error attempting to write lower page; rc = [r-28]"

The only thing I can think of is that my hard discs are getting pretty  full as I've been hahving a few issues with my Nextcloud sync client.

Any help would be much appreciated as due to the Nextcloud sync issues, I'm worried that not all of my baby pics are backed up.

Thanks in advance!

---

### Post by deadflowr on 2020-08-07
*Thread move to **MINT***

There a bug report about something like this here:
[https://bugs.launchpad.net/ecryptfs/+bug/1540035]("https://bugs.launchpad.net/ecryptfs/+bug/1540035")
Not sure how helpful that is, but it is something.

---

### Post by user-mane on 2020-08-07
thanks for the link. I found this earlier when looking for solutions but it doesn't seem to help really. I'm unable to login to Mint so I'm not sure what options that'll leave me with. I feel like if I had a way of deleting some files from the HDD then that may solve the problem but i'm guessing that them being encrypted won't allow me to do so.

---

### Post by deadflowr on 2020-08-07
What else have you looked at in regards to ecryptfs?
It helps to know so others don't inadvertently post something else you've seen or tried.

---

### Post by user-mane on 2020-08-08
sorry, I should have mentioned that in the OP. So, I did have a good search for the problem prior to posting but I couldn't find too much info. I found [forum posts]("https://forum.manjaro.org/t/ecryptfs-encrypt-page-error-attempting-to-write-lower-page-rc-4/76295/3") that weren't very informative. I understand that it's to do with the encryption system and have seen that some people mention that it may be not enough free space on HDD, a kernel problem and even that ecryptfs is creating too many logs.

The problem is that I am very much a linux beginner. I've slowly figured out a lot of stuff over the last couple of years but this seems a bit over my head as i'm unable to login to start fixing the problem.

---

