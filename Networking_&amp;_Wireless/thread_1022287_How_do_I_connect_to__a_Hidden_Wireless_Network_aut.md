---
title: "How do I connect to  a Hidden Wireless Network automatically?"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by andrewwg94 on 2008-12-26
I use Wi-Fi on the ps3. and the only way to connect to a wi-fi network is by using 'connect to hidden wireless network' even though my network isn't hidden. anyway, how do i connect to a hidden network wirelessly?

---

### Post by BrandonBan6 on 2008-12-26
System > Preferences > Network Configuration

Add your network to the wireless tab, edit that network, check the the checkbox that says "connect automatically".

---

### Post by andrewwg94 on 2008-12-26
it's already there :(

---

### Post by superprash2003 on 2008-12-26
so it doesnt connect automatically inspite of that?

---

### Post by andrewwg94 on 2008-12-26
> **superprash2003 said:**
> so it doesnt connect automatically inspite of that?

no

---

### Post by igarvey on 2008-12-27
I have the same problem, I believe this might be a bug.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/295796](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/295796)

---

### Post by JobeJahova on 2009-05-03
I have the same problem. The network is hidden. I connect to my hidden network with no issues. Then I go to the System > Preferences > Network Connections. There, I click Wireless > "network name" > Edit > Connect Automatically is checked. Still, when I log out and in I am not automatically connected.

Please help.

---

### Post by kaumell on 2009-07-07
Any update or further info on this.

I'm looking to place Ubuntu on a number of wireless carts to connect to a terminal server, but simply can't expect my users to through connecting to the hidden network.

Thanks

---

### Post by aevans90 on 2011-01-06
I had this same problem and found that deleting the SSID, left click once, and use only the connect to hidden wireless button. for some reason it wont work unless thats  what you use.

---

### Post by vincix on 2011-02-12
Isn't there a command line script that you can make in order to connect automatically to a wireless network and override the gui network application?

I for one am trying to connect to a wless network with wpa security and I don't really know how to use the new wpa_supplicant which is now a directory rather than a file. I managed to do it in Slackware(!!), but couldn't in Ubuntu :)

---

### Post by kerry_s on 2011-02-12
you just have to check "available to all users"

---

### Post by vincix on 2011-02-13
> **kerry_s said:**
> you just have to check "available to all users"

I have actually tried this, but the only effect is that I am requested a password every time I try to connect (manually still). So it's even worse!

---

### Post by kerry_s on 2011-02-13
> **vincix said:**
> I have actually tried this, but the only effect is that I am requested a password every time I try to connect (manually still). So it's even worse!

you set the password manager with no password & you shouldn't have that problem.

---

### Post by vincix on 2011-02-13
> **kerry_s said:**
> you set the password manager with no password & you shouldn't have that problem.

It's the user's password, not the network password. I don't think there's any way round it. It would work probably if I ran X with root :/

---

### Post by kerry_s on 2011-02-13
> **vincix said:**
> It's the user's password, not the network password. I don't think there's any way round it. It would work probably if I ran X with root :/

no, 
go to preferences-> password & encrypt
right click passwords-> change password
put in your password & leave the other 2 blank
it will ask you if you want to store unencrypted, select "use unsafe storage".

when it says unsafe, it just means anyone with physical access could find the password in your hidden files if they looked.

---

### Post by vincix on 2011-02-13
> **kerry_s said:**
> no, 
go to preferences-> password & encrypt
right click passwords-> change password
put in your password & leave the other 2 blank
it will ask you if you want to store unencrypted, select "use unsafe storage".

when it says unsafe, it just means anyone with physical access could find the password in your hidden files if they looked.

It still doesn't work. It's the same as before. After I edited, my wireless reconnected (it's true that it didn't ask me for a password after I checked 'available for all users') but when I restarted ubuntu it didn't begin to connect and when I tried to edit the wireless network it asked for my linux user's password again.
Therefore, it's quite obvious that there's a gui bug and it doesn't work with hidden networks when you put it to connect automatically. So maybe someone might try explain to me (or give me a link towards a tutorial) how to create a command line script in order to make ubuntu connect automatically to my network; thing which I knew how to do under slackware, as i said before, but can't under Ubuntu, because the wpa_supplicant got more sophisticated or sth.

---

### Post by kerry_s on 2011-02-13
> **vincix said:**
> It still doesn't work. It's the same as before. After I edited, my wireless reconnected (it's true that it didn't ask me for a password after I checked 'available for all users') but when I restarted ubuntu it didn't begin to connect and when I tried to edit the wireless network it asked for my linux user's password again.
Therefore, it's quite obvious that there's a gui bug and it doesn't work with hidden networks when you put it to connect automatically. So maybe someone might try explain to me (or give me a link towards a tutorial) how to create a command line script in order to make ubuntu connect automatically to my network; thing which I knew how to do under slackware, as i said before, but can't under Ubuntu, because the wpa_supplicant got more sophisticated or sth.

mine is hidden, so it works fine there.

it's normal to ask for the password when editing connections.

you should not have to edit it if you set it up right the first time.

if it's wrong, don't edit, delete & do it again from the applet.
the reason being is it writes to a file, if you edit there could be more than 1 setting for the same network in the settings file, which confuses network manager causing problems like your describing.

---

### Post by vincix on 2011-02-14
> **kerry_s said:**
> mine is hidden, so it works fine there.

it's normal to ask for the password when editing connections.

you should not have to edit it if you set it up right the first time.

if it's wrong, don't edit, delete & do it again from the applet.
the reason being is it writes to a file, if you edit there could be more than 1 setting for the same network in the settings file, which confuses network manager causing problems like your describing.

I've done what you said. I've deleted it and created it again, having checked the 'available for all...' box and of course it still doesn't work. I don't know why you won't admit that there's a bug in the gui netw application :D I am not the only one who's got this problem and I had it in the previous version of Ubuntu, too and on another laptop etc. In Windows it works just fine. Sometimes, however, it does connect automatically after the booting (i don't know why exactly), but most of the times i just get the exclamation point and it doesn't even try to connect to any network. I can't imagine having missed anything, since there are a few options that I have to remember and the steps are obviously easy.

Later edit: Moreover, the 'available for all users' option is a spoke in the wheel, because every time it doesn't connect automatically (which is most of the tmie), I have to go to the 'connect to hidden network' and when I choose my network it asks for a password, which it doesn't when the 'available...' box isn't checked.

---

### Post by kerry_s on 2011-02-14
don't know, i have no problems, so i can't say if it's a bug or not.
at this point, i'd bet it's hardware related, perhaps not fully linux compatible. who knows? just another mystery. ):P

---

### Post by vincix on 2011-02-15
> **kerry_s said:**
> don't know, i have no problems, so i can't say if it's a bug or not.
at this point, i'd bet it's hardware related, perhaps not fully linux compatible. who knows? just another mystery. ):P
Maybe there are some incompatibilities with the hardware, but if you look up the problem on the internet, you'll see that it's not such rare case :)
As I told you before, I've had the same problem on another laptop with Ubuntu.

---

### Post by kerry_s on 2011-02-15
> **vincix said:**
> Maybe there are some incompatibilities with the hardware, but if you look up the problem on the internet, you'll see that it's not such rare case :)
As I told you before, I've had the same problem on another laptop with Ubuntu.

:lolflag: maybe it's you. (i am joking)
i would start at the router, try not hiding, try hidden without password, then with wep, etc..., see what happens.

i've seen routers do some funky things to wireless, some say they support wap, when it's actually only partial support, etc...

take step by step

---

### Post by vincix on 2011-02-15
> **kerry_s said:**
> :lolflag: maybe it's you. (i am joking)
i would start at the router, try not hiding, try hidden without password, then with wep, etc..., see what happens.

i've seen routers do some funky things to wireless, some say they support wap, when it's actually only partial support, etc...

take step by step

It works PERFECTLY under windows :/

Morever: I do want it to be hidden. I like it better this way. There are another 3 or 4 wireless networks in the block I live in and I simply don't want them (or any other) to see my wless network :)

---

### Post by kerry_s on 2011-02-15
> It works PERFECTLY under windows :/

of course it works, it's made for windows, they work with ms to make it work. 

did you think they work with linux to make it work? no! they don't care, we depend on some very smart people out there to reverse engineer the drivers an thus bring it to linux, not only that linux follows the standards that ms craps on.

the purpose of the router testing is to find the cause of the problem, my moneys on wap being the problem.

---

### Post by vincix on 2011-02-15
> **kerry_s said:**
> of course it works, it's made for windows, they work with ms to make it work. 

did you think they work with linux to make it work? no! they don't care, we depend on some very smart people out there to reverse engineer the drivers an thus bring it to linux, not only that linux follows the standards that ms craps on.

the purpose of the router testing is to find the cause of the problem, my moneys on wap being the problem.

You're probably right, but I don't know if it's so relevant to our discussion here, given the fact that I CAN connect to the network no problem in Ubuntu. I hope you did understand that. The only problem is that Ubuntu doesn't connect automatically. You can't put the responsibility on the router. I simply want Ubuntu to connect automatically, 'cause I can connect to my network otherwise. It's only that it doesn't connect automatically when it boots. It's as simple as that. That Ubuntu's problem, not the router's. It's quite obvious.

---

### Post by kerry_s on 2011-02-15
> **vincix said:**
> You're probably right, but I don't know if it's so relevant to our discussion here, given the fact that I CAN connect to the network no problem in Ubuntu. I hope you did understand that. The only problem is that Ubuntu doesn't connect automatically. You can't put the responsibility on the router. I simply want Ubuntu to connect automatically, 'cause I can connect to my network otherwise. It's only that it doesn't connect automatically when it boots. It's as simple as that. That Ubuntu's problem, not the router's. It's quite obvious.

thats what i'm saying it should do it automatically, something is causing it not to. i'm betting its your wap setup, thats why i suggested you trouble shoot.

first try not hidden, if it works there you go, thats the cause. if it doesn't than not the cause.

next test if it's the encryption, switch to wep, if it works than somethings wrong with wap.

etc...

it's up to you if you want to fix it, i just offer suggestions, you have to know the cause before you can even try to fix it.

---

### Post by vincix on 2011-02-15
> **kerry_s said:**
> thats what i'm saying it should do it automatically, something is causing it not to. i'm betting its your wap setup, thats why i suggested you trouble shoot.

first try not hidden, if it works there you go, thats the cause. if it doesn't than not the cause.

next test if it's the encryption, switch to wep, if it works than somethings wrong with wap.

etc...

it's up to you if you want to fix it, i just offer suggestions, you have to know the cause before you can even try to fix it.

I already know that the problem is the fact that it is hidden :/ This is what i was talking about from the very beginning: connect automatically to HIDDEN network :) That was the whole point. I want to connect automatically to a hidden network. If I do it with a script, it works, I'm sure of it. I've already done it in Slackware... So it's got nothing "against" linux and all that. I don't know what's more to say. Ubuntu should have solved it. This is my opinion.

---

### Post by kerry_s on 2011-02-15
> **vincix said:**
> I already know that the problem is the fact that it is hidden :/ This is what i was talking about from the very beginning: connect automatically to HIDDEN network :) That was the whole point. I want to connect automatically to a hidden network. If I do it with a script, it works, I'm sure of it. I've already done it in Slackware... So it's got nothing "against" linux and all that. I don't know what's more to say. Ubuntu should have solved it. This is my opinion.

the commands should be the same as in slackware, so just add your script, to /etc/rc.local it already runs as root so no sudo needed in script or command.

if you post the script, we can look it over to make sure it's ubuntu compatible.

---

### Post by Slave2Metal on 2011-02-15
If using network manager, wouldn't you input the network name, along with bssid and mac address.  Of course encryption password, if any.  This is how mine is set up on two different machines and it automatically connects my "hidden" network.  Along with automatic connect and available for all users.

Have you tried broadcasting ssid, connect with all the pertinent info, then disable broadcasting ssid?

---

### Post by vincix on 2011-02-17
> **Slave2Metal said:**
> If using network manager, wouldn't you input the network name, along with bssid and mac address.  Of course encryption password, if any.  This is how mine is set up on two different machines and it automatically connects my "hidden" network.  Along with automatic connect and available for all users.

Have you tried broadcasting ssid, connect with all the pertinent info, then disable broadcasting ssid?

I don't get it. Why does everyone look for problems outside the gui network application? In Windows works just fine (Ok, it a huge microsoft conspiracy, etc), but in Slackware always worked fine. 
There's nothing wrong with the router. 
Maybe you should try posting a tutorial or sth with instructions on how to connect through command line?

P.S. I did discover that if I disable/enable my wireless from my laptop button it starts to connect automatically. So it's obvious an Ubuntu problem and NOT exterior to it!

---

### Post by Slave2Metal on 2011-02-20
> **vincix said:**
> I don't get it. Why does everyone look for problems outside the gui network application? In Windows works just fine (Ok, it a huge microsoft conspiracy, etc), but in Slackware always worked fine. 
There's nothing wrong with the router. 
Maybe you should try posting a tutorial or sth with instructions on how to connect through command line?

P.S. I did discover that if I disable/enable my wireless from my laptop button it starts to connect automatically. So it's obvious an Ubuntu problem and NOT exterior to it!

Great, so you figured it out on your own!  Guess you can mark this thread solved, never mind, it's not your thread.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by vincix on 2011-02-20
> **Slave2Metal said:**
> Great, so you figured it out on your own!  Guess you can mark this thread solved, never mind, it's not your thread.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)


Ok, so I guess my problem was related to the /etc/wpa_supplicant.conf. It didn't cross my mind that I could create the file myself and that I didn't need it to have been there already. So that was the catch I've been looking for. 
Thanks, I'll try to make it work :)

---

### Post by alienjon on 2011-09-10
To clarify - for me at least - the problem started with me recently too but *only* after I set the router to a hidden broadcast.  When it is not hidden it works fine.  Switching it back was more appropriate for me than doing things manually (I actually stuck with Ubuntu for my laptop simply because of the wireless connectivity)

---

### Post by vincix on 2011-09-10
Yeah, well, Ubuntu has started working really badly since the last major upgrade and I'm giving up. You can't install a proper video driver unless you recompile your kernel and so on. Their video driver sucks. So for my part, I think that they've done a really bad job trying to make it a user-friendly os. They've got a lot to learn and Microsoft seems to have learnt it already more or less.

---

### Post by shelbydz on 2011-09-12
So reading this, it seems theres no real solution for a hidden SSID? I have 2 users on my laptop (me and my wife). I'm the primary user and I just created hers a few days ago. I can see the network manager icon at the top right to see the network status. But when I log in as my wife, I cannot see that. This means I cannot use it to make connections to hidden networks. 

If I broadcast my ssid, I can make it connect automatically and everything is good. If it's hidden, my wife's user has no way to connect to the network. 

Thoughts??

thx

---

