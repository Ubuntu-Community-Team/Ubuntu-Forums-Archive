---
title: "Running Newist 32 bit (only with some wireless cards) wireless lan"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by JKSully on 2012-04-22
If you have problems with Cisco wireless cards. when logged into terminal type: sudo modprobe ndiswrapper
then:
(your password)

and you are not finished if you have and using kde wallet type your wallet passwrd in after you go to connection statuses and click on Lan(Wireless). (Your creating your kde wallet the first time you access this information)
Then go to your network and double click on yours when picked up.
Then go to copy BSID on first page.
On Security PAge click on what type of router you have(most common WPA/WPA2personal ) then type in your routers password
Click: Apply then OK
Should prompt you to use kde wallet so type in your password  
watch for:
Configuring Interface
Setting Network Address
And last... Connected
Easy to remember steps and for fall back because the only problem is every time you restart or hibernate or sleep your computer you must repeat.
 If you can't add a wireless network

Open Terminal
type 'sudo modprobe ndiswrapper'
when asked for passwd, type it in
then add wireless network
through icon in lower right screen
(next to clock)
(manage connections)
add new connections then click scan
select yours
set up security
copy AP to BSSID
click OK
click Apply
click Netowkr Manager and click on network wish to connect

---

