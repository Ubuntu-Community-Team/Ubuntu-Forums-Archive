---
title: "DSL Connection with wireless access"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by mrt_doulaty on 2010-05-21
I've recently upgraded to 10.04 LTS, it is great.
I've a problem, and that is:
I've a wireless network (with local access only), I can easily connect to it, but in order to connect to internet, I should establish a DSL connection, I've created the DSL connection and when connecting my notebook to the wired LAN,  in the network menu, I can easily select "DSL connection 1" and connect to it, but in case of wireless access to the same network the "DSL connection 1" does not appear in the list so that I can connect to it. Any help would be highly appreciated.

---

### Post by iponeverything on 2010-05-21
your dsl is probably pppoe. Many wireless routers will handle this fine, configure the wireless router to bring up the connection. 


btw -- from your post it not at all clear what is going on, and my skills as a psychic are getting rusty -- 

Is there a wireless modem and dsl modem? Is the the wireless modem also the dsl modem?

---

### Post by mrt_doulaty on 2010-05-21
Sorry for my poor description!

I know I can setup my modem to connect automatically, without needing to establish a connection manually.
But I configured my ADSL modem (which is a router and a wireless modem) to use bridging.

In Windows, I can create a ADSL connection and connect to internet using that connection. No matter how the notebook is connected to the local network, using it's wireless adapter or wire.

In Ubuntu when I plug the cable, I can see the DSL connection and can connect to it, but when connecting to my local network using wireless adapter, the DSL connection does not appear in the menu.

Hope it was clear enough.

Thanks for your help.

---

### Post by mrt_doulaty on 2010-05-21
>>Is there a wireless modem and dsl modem? 
Yes
>>Is the the wireless modem also  the dsl modem?
Yes

---

### Post by iponeverything on 2010-05-21
thanks, you have it cleared up.

From looking at the results of the below google search, this is a road that others have traveled before you..

[http://www.google.com/search?hl=en&source=hp&q=ubuntu+pppoe+over+bridged+wireless](http://www.google.com/search?hl=en&source=hp&q=ubuntu+pppoe+over+bridged+wireless)

---

### Post by mrt_doulaty on 2010-05-21
I've gone that way before, the problem with pppoeconf is that: my username have some trailing spaces, when I enter my username there, it trims it and removes the trailing spaces from it, but when configuring DSL connection with Network Manager, it is OK, but as I said before, I can not see my DSL connection in the menu when connected through wireless, in other words, let me say in this way: how can I connect to the DSL connection that I created using Network Manager in shell?
(pppoeconf uses 'pon' command to establish a connection)

---

### Post by iponeverything on 2010-05-21
slowly but surely ;)

In your /etc/ppp/pppoe.conf

does putting quotes around your account name preserve the trailing spaces?


```
ACNAME="youraccount "
```

---

### Post by mrt_doulaty on 2010-05-21
> **iponeverything said:**
> slowly but surely ;)

In your /etc/ppp/pppoe.conf

does putting quotes around your account name preserve the trailing spaces?


```
ACNAME="youraccount "
```


Already tried 'chap-secrets' files, but no lock!

Where are the configuration files for DSL connections that are created with "Network Connections" are stored? And to ask again, how they can be dialed manually using shell?

---

### Post by iponeverything on 2010-05-21
If anyone else wants to pick this one up, feel free, I don't have the energy or motivation to follow up on it. 

@mrt_doulaty don't give up, the truth is out there. Google is the best thing since the Oracle of Delphi, the key is knowing the right questions to ask. 

If you install gconf-editor you can access and modify the settings for Network Manager connections. They are stored in a structure disturbingly similar to the windows registry.     

install it with:

```
sudo apt-get install gconf-editor

```

after it's installed you can dig it up from one of the system menus or fire it from the terminal with the command:

```
gconf-editor
```

For starting network manager connections via the shell, it is possible though small python utility downloaded from here:

[http://vidner.net/martin/software/cnetworkmanager/](http://vidner.net/martin/software/cnetworkmanager/)

Install like so:

```
sudo make install
```

basic usage is:

```

cnetworkmanager --wifi=on
cnetworkmanager --wifi=off

```

It just pushes the right dbus buttons for you.

Read the documentation included in the package and from the site for more information on usage. It is written in python, so you can modify it for special cases if need be -- though you should be warned that dbus is a hairy beast that does not give up its secrets without your paying a toll in time and effort.

The above is just answers to your questions below, you should note that none of it is relevant to solving your problem -- I just decided what the heck, I'll just put information out there again and maybe it can help someone solve an issue totally unrelated to the problems your having. You are welcome go down this path, but it's a dead end as far as your issue is concerned.

That said, my intuition is that your problem is fairly easy solve, so when you come across the solution add it to this thread so that others can find it when they ask Google the Great. 

Sorry, but as easy as the solution may be -- I am brain dead and have not had to mess with pppoe in last few years.

I hope you decide to stick with Linux, though in the future when trying to solve problems provide all the information up front. It is quite frustrating to have important details trickle out little by little. You don't want to make it too difficult for person trying to help you out. 

note you provided new details in posts:

#1, #3, #6 and #8 -- 

good luck :)

> Already tried 'chap-secrets' files, but no lock!

Where are the configuration files for DSL connections that are created with "Network Connections" are stored? And to ask again, how they can be dialed manually using shell?

---

### Post by mrt_doulaty on 2010-05-21
Thanks, cnetworkmanager is the right thing, I think!

But I've some minor problems using it, as I understood, I should use '--activate-connection' to activate a connection, this needs an ID.
The ID can be acquired by '--con-info='. Is that right?
Now I have a system connection named 'DSL connection 1'
How can I get its ID?

Here is my system connections strings:
Active | Name             | Type          
-------+------------------+---------------
       | VPN connection 1 | vpn           
*      | Auto eth0        | 802-3-ethernet
       | DSL connection 1 | pppoe

---

