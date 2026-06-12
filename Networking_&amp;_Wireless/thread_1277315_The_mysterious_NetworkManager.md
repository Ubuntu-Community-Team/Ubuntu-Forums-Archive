---
title: "The mysterious NetworkManager"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by jago25_98 on 2009-09-28
I'm connecting to a wireless network where the DHCP isn't working for some reason. I need NetworkManager because configuring it all by hand is a nightmare, especially when I move the laptop to a new network. NetworkManager starts to connect for me but then fails because the DHCP request from dhclient fails, I found this out from $tail /var/log/daemon.log
When the DHCP request fails it prompts me for the WiFi key again, making me think I've typed the wrong key in (I thought I had the WPASupplicant problem when I didn't!), when I haven't typed in the wrong key at all.. After a while it then connects to another network I didn't want to connect to at all. 

I've also no idea where NetworkManager stores it's config files... can't see anything in /etc? I have about 50 configs leftover from previous connections I'd like to tidy up. 

Can't see any documentation about how NetworkManager works behind the scenes?

NetworkManager also doesn't list an option for 64bit keys either. Perhaps I should try something else? I need something graphical and easy, especially for wireless connections, but it needs to clearly say what it is doing. What package would you recommend as an alternative?

So, to summerise those questions:

1) Where can I find documentation on how NetworkManager works?
2) Where do I specify a static IP?
3) Where does NetworkManager does it's config files?
4) Do you know a better alternative?

Thanks. I'm sure other people must have been having problems with it.

---

### Post by t0mppa on 2009-09-28
> **jago25_98 said:**
> 
So, to summerise those questions:

1) Where can I find documentation on how NetworkManager works?
2) Where do I specify a static IP?
3) Where does NetworkManager does it's config files?
4) Do you know a better alternative?

1) [This]("http://live.gnome.org/NetworkManager") will at least get you started.

2) Right click the icon on Notification Area and choose *Edit Connections...*, then go to wireless tab and you can edit an existing connection or create a new one.

3) ~/.gconf/system/networking/connections/

4) WICD is pretty popular around here, although some people hate how it doesn't integrate into the notification graphics and it isn't perfect either. You can Google up a few others as well, if you want a more thorough list.

---

### Post by trundlenut on 2009-09-28
Network manager just doesn't work on my laptop so I used wicd instead, it's in the repositories, maybe give that a try instead.

In my case I think the problem is related to using WPA encryption and the rather old wireless card I have but it works without problem using wicd.

Oh and you can use gconf-editor to look at the config data for network manager.

---

### Post by gordintoronto on 2009-09-28
Can other computers connect to the router with DHCP?

---

### Post by bab1 on 2009-09-28
> **jago25_98 said:**
> ... Can't see any documentation about how NetworkManager works behind the scenes?

NetworkManager also doesn't list an option for 64bit keys either. Perhaps I should try something else? I need something graphical and easy, especially for wireless connections, but it needs to clearly say what it is doing. What package would you recommend as an alternative?

... 
1) Where can I find documentation on how NetworkManager works?
2) Where do I specify a static IP?
3) Where does NetworkManager does it's config files?
4) Do you know a better alternative?

Thanks. I'm sure other people must have been having problems with it.

See [**_Controlling NetworkManager_**]("http://www.arachnoid.com/linux/NetworkManager/index.html") for a good description.

---

### Post by chili555 on 2009-09-28
> 2) Where do I specify a static IP?Right click the Network Manager icon, select Edit Connections, then Wireless and IPv4 settings. You will have the option to change 'DHCP' to 'Manual.' Fill in all the details, save and close. You should be all set.

---

### Post by bigboy7foru on 2009-09-30
ok so on step 4 is that a file path cause if so it doesnt exist on my computer
 
also i can't find files where the network connection should be at.
 
I don't know what the layout of the file looks like either

---

### Post by trundlenut on 2009-09-30
you need to add the configuration editor to easily view the config files, you can add it to the system tools menu and then you will be able to see the files with the network config in.  I think gconf-editor uses xml files IIRC.

I don't really understand what your asking about No.4, wicd is an alternative to network manager, you need to install it.

---

### Post by jago25_98 on 2009-10-03
Thank you everyone. It's so simple; just right click and click edit connections. 

At first I didn't think to right click it and then when I did I thought that this was for editing the current connection only. I then clicked About and got no help page, I then clicked the website and got no help. 

I've written to the mailing list making some suggestions to make it clearer how to use NetworkManager, including adding the info to the webpage and a help button. I might try to write some documentation for it too...

 but frankly I'm not sure whether I will if that documentation has to be exhaustive first time - I think it's better to have bullet points of info listed first like in tutorials we see online rather than nothing at all   - whereas the documentation I see actually built into Ubuntu I find tends to describe how to do simple things in excruciating detail. When we get to the info we really need the writer has run out of steam and the documentation ends! - why not just get permission and copy and paste from the web and put up with inconsistency and hard to readability in favour of at least having some docs for the user.

---

### Post by jago25_98 on 2010-10-02
A year later and what seems like a similar problem:

Define a 3G access point in `edit connections` and it doesn't come up as an option t oconnect with the *left *click

---

