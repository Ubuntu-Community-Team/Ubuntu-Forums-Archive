---
title: "pppoe help"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by voteforcondit on 2010-05-30
lastnight i got a pppoe wireless to work useing pppoe conf now i cant get it to work again after restarting laptop. how do i reconnect? im sure this is an obvious answer

---

### Post by puppywhacker on 2010-05-31
first you have to connect to the wireless, then you should be abled to reach the website from your wireless router something like [http://192.168.1.1/](http://192.168.1.1/)

Next you have to do a PPP dial-up, you can do that in several ways, one is to use the network manager (network icons in the right top) or on command-line with wvdial.

Can you specify in which parts it fails? what do you do, and what are the responses?

---

### Post by voteforcondit on 2010-06-02
network manager says. device not managed

---

### Post by sites on 2010-06-02
I recently configured a laptop for PPPoE through terminal using pppconfig and then 'pon dsl-provider'.  Are you setting up PPPoE on a wireless router?  In that case i didn't think you would need to configure this on the pc.

---

### Post by voteforcondit on 2010-06-04
so i now have this exact problem on 2 computers in the house

both i got set up to connect to our dsl wireless modem the way i got them to  to connect i first connected to the network via wireless useing network manager then ran pppoe conf and they set up super easy and net worked great

then i went to sleep
and shut down 

next morning boot up both computers and network manager on both says "device not managed" under wireless where do i go from here?????

computer one is a hp laptop running xubuntu jj

computer two is a amd 64 running ubuntu jj

---

### Post by sites on 2010-06-04
Sorry to push the issue but i'm confused.  You're using a dsl gateway modem with built-in wifi, correct?  Why isn't PPPoE setup on the gateway?

---

### Post by voteforcondit on 2010-06-04
idk its a dsl modem built in wifi 
i dont know how its set up
when doing it from windows you have to connect to the wireless then connect to the dsl diffrently
its not my modem to mess with so i cant change the way its set up 

thats how i got it to work before i just dont understand why after a restart it won't work at all

---

### Post by dineshs on 2010-06-04
Can you post the contents of /etc/network/interfaces
```
gksudo gedit /etc/network/interfaces
```
Let it contain only this
```
auto lo
iface lo inet loopback
```
Now try to run pppoeconf and let us know the result
Also pl ask your ISP whether your modem can be configured in PPPoE mode(store username and password in modem so that you need not always use pppoeconf or pon...ie your connection will be Always on)

---

### Post by voteforcondit on 2010-06-04
computer 1 when i put in that first code nothing happens. 
it asks for my password then back to nothing
it dosnt open up a script or anything


i found the script on in the file system it wont let me save



computer 2

when i put in the first code it brings up a blank file so i put in the part you said
i go to save it says there is no file with that name 
when i go find it manualy and open it it wont let me save

---

### Post by dineshs on 2010-06-04
please try
```
sudo gedit /etc/network/interfaces
```
and proceed

---

### Post by sites on 2010-06-05
> **voteforcondit said:**
> idk its a dsl modem built in wifi 

Ok.  I suggest the following.  Link one of your computers directly to this DSL modem via ethernet.  Configure the modem through your web browser.  The typical way of doing this is by typing 192.168.1.254 in the address bar.  Sometimes these modems use a different default address, but you should be able to determine this with the network manager.  Find the PPPoE configuration (probably in Advanced settings or something similar).  This is where you enter your account name and password for your service.  Also make sure you find the "Always on" setting in there somewhere.  Then check the DHCP configuration and make sure it's automatic.  Wireless security is also an option to consider.  All of these settings are on the modem/gateway instead of the computer.

With this kind of setup, the DSL modem handles all the work and you don't have to fiddle with PPPoE on every computer that connects to your network.  All you'll have to do is hook up to the LAN or wifi.

---

### Post by voteforcondit on 2010-06-07
ok that works fine but thats not solving my problem
with my wireless device not working through the network manager i cannot access the wireless network to sign onto the dsl with. i tried reinstalling network manager and it didnt help....

---

### Post by voteforcondit on 2010-06-07
anyone? should i look for drivers or something ??

---

### Post by dineshs on 2010-06-08
> **voteforcondit said:**
> ok that works fine but thats not solving my problem
with my wireless device not working through the network manager i cannot access the wireless network to sign onto the dsl with. i tried reinstalling network manager and it didnt help....
If your problem is wirelesss I think it is better to start a new thread with that heading so that experts on this forum can help.Pl refer
[http://ubuntuforums.org/showpost.php?p=6183681&postcount=1](http://ubuntuforums.org/showpost.php?p=6183681&postcount=1)

---

