---
title: "connecting to wireless internet help (using hp mini)"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by bnr18241 on 2009-12-24
ok so i just got an hp mini 110 netbook and ubuntu 9(the koala one). i have no clue how to connect to a wireless internet connection. the wifi switch on my computer is orange and i dont know if that means its on or off. when i run windows 7, wireless works just fine and the switch is white. whenever a move the switch it just stays orange. but anyway no wireless networks show up when i go to the network connections screen. i basically have no idea what the hell im doing and i dont know how to connect. help!!!

---

### Post by focwiz on 2009-12-24
> **bnr18241 said:**
> ok so i just got an hp mini 110 netbook and ubuntu 9(the koala one). i have no clue how to connect to a wireless internet connection. the wifi switch on my computer is orange and i dont know if that means its on or off. when i run windows 7, wireless works just fine and the switch is white. whenever a move the switch it just stays orange. but anyway no wireless networks show up when i go to the network connections screen. i basically have no idea what the hell im doing and i dont know how to connect. help!!!

My HP MINI 110 required me to connect with a wired connection and download the Broadcom STA driver.  Once installed (it will show up in System>Hardware Drivers) wireless configured normally.

---

### Post by bnr18241 on 2009-12-24
> **focwiz said:**
> My HP MINI 110 required me to connect with a wired connection and download the Broadcom STA driver.  Once installed (it will show up in System>Hardware Drivers) wireless configured normally.
Where did you download it?

---

### Post by focwiz on 2009-12-24
> **bnr18241 said:**
> Where did you download it?

[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by bnr18241 on 2009-12-24
> **focwiz said:**
> [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
i downloaded it and everything...but im not quite sure what to do next because 2 folders called lib and src came up

---

### Post by danastasio on 2009-12-24
What is the output of
```
lspci
```

---

### Post by focwiz on 2009-12-24
> **bnr18241 said:**
> i downloaded it and everything...but im not quite sure what to do next because 2 folders called lib and src came up

Go to System>Hardware Drivers ...it should search and find the STA driver...click activate..(I think yoou still have to be connected via wire for this)

---

### Post by bnr18241 on 2009-12-24
> **focwiz said:**
> Go to System>Hardware Drivers ...it should search and find the STA driver...click activate..(I think yoou still have to be connected via wire for this)
ok i did that but there are still no wireless networks coming up

---

### Post by bnr18241 on 2009-12-25
> **focwiz said:**
> Go to System>Hardware Drivers ...it should search and find the STA driver...click activate..(I think yoou still have to be connected via wire for this)
nevermind i finally got it working...thanks for your help

---

### Post by olivia751 on 2009-12-25
Hello bnr18241,

                       You can also get help from this site if you still facing the same problem.

[http://www.microsoft.com/athome/organization/wirelesssetup.aspx](http://www.microsoft.com/athome/organization/wirelesssetup.aspx)

This is helpful for internet connection relates problem. I hope it will help you.
Marry Christmas.




Regards,
Olivia



     [Web Security & Video Conference UK]("http://www.newtonit.co.uk/")

---

