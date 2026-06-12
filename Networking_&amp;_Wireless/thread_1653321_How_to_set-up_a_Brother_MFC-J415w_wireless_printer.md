---
title: "How to set-up a Brother MFC-J415w wireless printer in 64 bit"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by electrojustin on 2010-12-26
As I have recently figured out, it is very hard to set-up a Brother MFC-J415w wireless printer on a 64 bit machine, so to save you from spending hours searching the Internet and trying different drivers, I will tell you how to set one up.

Step one: Download the 32-bit driver from this link: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J415W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J415W). When prompted, save the file.

Step two: Open the terminal and type in the following commands: ```
mkdir /usr/lib/cups
``````
mkdir /usr/lib/cups/filter
``````
mkdir /usr/share/cups/model
```Depending on what you've tried before, some of these directories may already exist.

Step three: Type the following commands:
```
sudo -s
``````
cd Downloads
``````
mkdir /var/spool/lpd
``````
dpkg -i --force-all mfcj415wlpr-1.1.1-1.i386.deb
```Step four: Type the following commands in: 
```
cp /usr/lib/cups/filter/brlpdwrapper* /usr/lib64/cups/filter
``````
cp /usr/lib/libbr* /usr/lib32/
```Now you are ready to print. Adding a printer in System->Administration->Printers is not necessary as it should already be there.

---

### Post by hyperair on 2011-06-30
I've actually found that dpkg -i --force-architecture *.deb was good enough for me. None of that mkdir and cp'ing around files was needed. 

In fact, the hardest part was finding the download link for the driver, which I managed to by following your link. Thanks!

---

### Post by electrojustin on 2011-11-03
As it turns out, as of recent versions of ubuntu and the driver, much of the mkdiring cps are unnecessary. All that is needed is for you to download the 32bit driver and cupswrapper and force install them. Also, the printer it automatically adds will probably not work, so delete it and set it up through "printing" manually.

---

