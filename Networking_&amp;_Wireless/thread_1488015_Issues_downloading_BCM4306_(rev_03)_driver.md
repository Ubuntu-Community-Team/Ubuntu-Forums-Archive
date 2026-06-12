---
title: "Issues downloading BCM4306 (rev 03) driver"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by mcraul on 2010-05-19
I just installed the newest version of Ubuntu onto a Gateway laptop that is using the Broadcom BCM4306 (rev 03) driver. I have been following the steps in this post 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver)

but when I try to download the driver using this command and location

```
wget http://myspamb8.googlepages.com/Driver_3607.zip
unzip Driver_3607.zip
```

It looks like it downloads but when I do a 

```
ls -al
```

and search for the file it looks like this

```
rw-r--r--  1 raul raul 308432 2010-03-01 19:25 Driver_3607.zip?attachauth=ANoY7crXT9NqEsrO4yHuYxYWykfx7KBKnAmSin3ozoTRWJAa4SSRIJrqPem4QWw7kuVG5Joc7cJVo8cOemPgYI5MhlyuQEPr522Y1ZCxZ5XJEn0mcJW0xX0TK4VnGTm2uslQ3tH3-FvQeCtOL515V36_AMYDgg8rBfZri2jblKpDIUTTHF9ZOeyRyOm8cQQ7twa6UIWNQD2n&attredirects=0

```

So I cant unzip this. 
Anyway to overcome this?

Thanks!

---

### Post by chili555 on 2010-05-19
Please do:```
mv Driver_3607.zip\?attachauth\=ANoY7crWAQ2zCvpHaNzPp_8O75s1GLmae8mSh_g4ZjFx6yqmowtCYTXLSJFhw-5TK7L-XPeqFlRVmVdfkt8DtVx_Qo1Wwsk3BuKHT5lJ68vcKt1JxdgDDVzMLpgyGjkawvKHmHruoyT3Zsg7z-3dweFCiEf0Uz_kN4shGFOKscwANHphhhdKqCuM2VaSfG4uMaiWexrBuw29\&attredirects\=0  Driver_3607.zip
unzip Driver_3607.zip
```In other words, we just renamed it and unzipped it.

---

