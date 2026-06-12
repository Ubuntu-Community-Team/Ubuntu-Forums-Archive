---
title: "Cannot connect to auto etho1"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by Warren1482 on 2010-09-07
I just downloaded the lastest version of ubuntu to my compaq laptop. I then proceeded to plug in my ethernet cable to establish an internect connection. Under wired connection, it says auto etho1 but, the computer will not connect to it and I have no internet connection. Can somebody please help me? This is very frustrating. Thanks a lot.

---

### Post by wesleybailey on 2010-09-07
Hello Warren,

auto eth0 means that Ubuntu will try to configure the network adapter automatically. This tells me that Ubuntu has correctly detected the network card. So the next step would be to figure out if your are receiving an ip address from the modem, or your router. 


Open a terminal a type this command, then send me the output

```
ifconfig
```

Or graphically System->Administration->Network Tools and tell me if anyof the network devices have an ip address


Latest Tutorial:[convert uif to iso with linux]("http://wesleybailey.com/articles/uif-to-iso-converter")

---

### Post by Warren1482 on 2010-09-07
Yes I tried ip config and I got an ip address. I tried to type it in manually but I couldnt figure out how to do it because it wouldnt let me type in any letters. I am not sure if that would even work anyway. Thanks

---

### Post by wesleybailey on 2010-09-07
Please tell me what the ip address was, does it look like one of the following?

127.0.0.1 
192.168.1.100
169.x.x.x 

Please tell me the specific ip address you received, it matters

---

### Post by Warren1482 on 2010-09-07
I am not on the actual computer now becuase I am at work but if I recall correctly, it was 4 spaces with a combination of letters and numbers

---

### Post by Warren1482 on 2010-09-07
ok my ip address is fe80::216:d4ff:fe44:9a58/64

can someone please help me?

Thanks

---

### Post by wesleybailey on 2010-09-07
hmm, that appears to be an iv6 ip address. Could you post the entire output from the ifconfig command please.

---

### Post by Warren1482 on 2010-09-07
I dont have any internet on that computer so I dont know how I would post the output. I am using a different computer to talk to you. Please help. Thanks

---

### Post by Warren1482 on 2010-09-07
maybe this will help:

HWaddr 00:16:d4:44:9a:58

does this help?

---

### Post by wesleybailey on 2010-09-07
Ok, in the display does it have an inet address

like this one?

inet addr:192.168.16.28

---

### Post by Warren1482 on 2010-09-07
Yes. I see

inet addr:127.0.0.1


hope this helps. thanks a lot

---

### Post by wesleybailey on 2010-09-07
127.0.0.1 is the loopback address so that is not going to help, or work.

is there any interfaces listed? other than the lo

i,e is there any eth0 or eth1

Latest Tutorial: [convert uif to iso]("http://wesleybailey.com/articles/uif-to-iso-converter")

---

### Post by Warren1482 on 2010-09-07
Yes there is an eth0 listed. i see:

HWaddr 00:16:d4:44:9a:58

inet6 addr: fe80::216:d4ff:fe44:9a58/64



Hope this helps. Thanks a lot

---

### Post by wesleybailey on 2010-09-07
Ok, to me it seems that the eth0 is not receiving an ip address which you need.

Lets try releasing and renewing your ip, which your router should provide

release the ip
```
sudo dhclient -r
```


renew the ip
```
sudo dhclient
```

then run ifconfig eth0

and see if there is an inet address

---

### Post by Warren1482 on 2010-09-07
when I tried to do the command:

sudo dhclient -r


the computer said- [sudo] password for warren:

I tried the password I used to start up my computer but it doesnt let me type letters in the box. Do you know what the [sudo] password is?


Thanks

---

### Post by wesleybailey on 2010-09-07
the sudo password is the same password you use to log onto the computer. Unless someone else uses the computer, then it might be their password.

Try your password again, make sure you don't have caps lock on

---

### Post by wesleybailey on 2010-09-07
I will be Away from the computer, try what I have said so far. I will reply as soon as I am back.

wes

---

### Post by Warren1482 on 2010-09-07
I tried using my password for the computer and it says sorry try again. What should I do now?

Thanks a lot

---

### Post by Iowan on 2010-09-07
As a quick side-check, CTRL-ALT-F1 should open a TTY that requires a login - see if your username/password is successful. CTRL-ALT-F7 will get you back to the GUI.

---

