---
title: "Tether Works4 UbSftCntr Only"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by Uubo on 2011-02-06
I'm using easytether for my android phone, on Ubuntu 10.10
It works, acting in the terminal exactly as the [tutorial here]("http://androidforums.com/evo-4g-support-troubleshooting/146871-easy-tether-ubuntu-10-04-a.html") shows.

But it isn't recognised via the network connection icon (the one in the upper right corner), or System > network connections/proxy.
**Though ubuntu software center downloads 200Mb programs through it just fine**!  :confused: 

Anyone have any idea how I can convince Ubuntu that software center is correct, I do in fact have internet access?

---

### Post by robsoles on 2011-02-07
Welcome to UF.

So you are typing```
cd /usr/bin
easytether enumerate

```into one terminal and then, into another terminal```
sudo dhclient easytether0
```And at the point of being given a 'bound' IP address the Ubuntu Software Centre 'sees' the connection.

Let's verify that only Ubuntu Software Centre can 'see' this connection - I imagine you've opened a browser and gone for good old [www.google.com]("http://www.google.com") from it, please say so and that it did not resolve.

Please post back results of following commands in terminal ('passive' commands, they ask for info, they don't set anything...)```
ifconfig /a
nslookup www.google.com
```
Please copy and paste the results of the commands I have given you into your reply using this format: [noparse]```
<PASTED-CONTENT-HERE>
```[/noparse] to make it very easy to read and to distinguish between your text and 'system' text```
<PASTED-CONTENT-HERE>
```

---

### Post by Uubo on 2011-02-07
Alright I couldn't solve the issue.  I did try accessing google through the terminal (as well as chrome/firefox), no go. 

```
ifconfig /a
/a: error fetching interface information: Device not found
```


```
nslookup www.google.com
```
returned a "connection timed out" error

Furthermore I couldn't get ubuntu software center to any longer download through easytether on my phone.  Lacking even reproducible forms of failure I opted for a new solution.


Proxoid turned out to be an easier solution.  The instructions on the main site lead to an SDK that lacks a critical file "adb".  It has to be downloaded through eclipse with the rest of the android operating system, and is a major headache.  

I haven't tried pdanet for Ubuntu, but these were enough of a headache that I'd recommend trying it before either of these.


Also, thank you very much robsoles for your reply.  I appreciated how willing you were to help.

---

### Post by robsoles on 2011-02-07
Sorry:
```
ifconfig -a
```

---

