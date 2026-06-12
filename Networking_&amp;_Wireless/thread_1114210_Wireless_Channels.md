---
title: "Wireless Channels"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by SilverXill on 2009-04-02
Hello,

I am using 8.10 on my laptop and PC (PC set as dual boot) and i can't access the internet, my ISP has recnetly hanged my channel from 11 to 15, i can't seem to find my wireless network when i am looking at the wireless networks available or change the wireless netowrk using "**$ iwconfig ath0 channel 15**".

Any help or ideas ?

---

### Post by chili555 on 2009-04-02
Is there a channel 15? What does this tell us?```
sudo iwlist ath0 channel
```

---

### Post by SilverXill on 2009-04-02
That there are channels 1 to 11 but there are 15 channels, as i am in the UK and my USB dongle/Stick connects fine.

Not the onboard Wireless card (on my laptop which is an acer 5315)

---

### Post by coffeecat on 2009-04-02
> **SilverXill said:**
> i can't access the internet, my ISP has recnetly hanged my channel from 11 to 15, i can't seem to find my wireless network

Who is your ISP? This might sound a silly question, but is it a wireless service? Or do your have an adsl or cable service with your own wireless modem-router? Just need to clarify this.

Are you sure about channel 15?  [See Wikipedia]("http://en.wikipedia.org/wiki/List_of_WLAN_channels"). Channels 1-13 are in use in the UK, but some wireless equipment will not work with channels 12 and 13 because it is designed primarily for use in the USA. Perhaps your onboard wireless card comes in this category.

---

### Post by SilverXill on 2009-04-02
My ISP is O2.

It's an ADSL line with it's own router, it's made for wireless i do believe.

I'll double check the channel and reply back as soon as i got it.

---

### Post by coffeecat on 2009-04-02
> **SilverXill said:**
> My ISP is O2.

It's an ADSL line with it's own router, it's made for wireless i do believe.

I'll double check the channel and reply back as soon as i got it.

I thought that might be the case. In which case, your ISP didn't change the channel. You can do that yourself, but probably only within the range 1-13. Or if the ISP supplied you with a pre-configured router, you can change the settings yourself.

Just go into the web interface by typing its internal IP address (usually something like 192.168.1.1 or 192.168.0.1. or 10.0.0.1 - the manual will tell you) in a browser, logging in and changing the wireless channel somewhere under WLAN settings.

What make is the wireless modem-router?

---

### Post by SilverXill on 2009-04-02
it's one made by O2 i can't seem to find somewhere in the router options to change the channel. 

Router is a Thomson TG585v7

---

### Post by SilverXill on 2009-04-02
i managed to check the channel using my Ubuntu on Pc and it's channel 13, so i'm going to try to change the channel on my laptop to see if it'll detect it.

---

### Post by SilverXill on 2009-04-02
it won't let me change to channel 13, it's not in "iwlist ath0 channel" any other ideas ?

---

### Post by coffeecat on 2009-04-02
> **SilverXill said:**
> it's one made by O2 i can't seem to find somewhere in the router options to change the channel. 

Router is a Thomson TG585v7

It'll be in there somewhere. Can you log in to get into the web interface? It will be in the 'wireless' section somewhere - of course. :wink: Probably on the same page where you set the SSID, and WEP/WPA passphrase. Just keep looking.

---

### Post by coffeecat on 2009-04-02
> **SilverXill said:**
> it won't let me change to channel 13, it's not in "iwlist ath0 channel" any other ideas ?

No, that's not what you want to do. :shock: You have to change the channel in the modem-router setup. Your wireless software in Ubuntu will find the channel automatically.

But **Don't** use channel 13. Some equipment can't use it. Use somewhere between 1-11. 6 or 7 would be good.

---

### Post by SilverXill on 2009-04-02
the router already came set up with everything needed so i didn't have to go through anything, i'll keep a searching and let ya know :)

---

### Post by SilverXill on 2009-04-02
oki dokes, i found it, i'll change the channel before i go to bed as the whole house is using the network, sorry for the confusion :)

the reason why it was changed from 11 to 13 was cause there's a lot of wirelss in the area.

Thanks for the help :)

---

### Post by coffeecat on 2009-04-02
> **SilverXill said:**
> the reason why it was changed from 11 to 13 was cause there's a lot of wirelss in the area.

Yes, if there are neighbours using the same channel it can affect your connection.

By the way, are you allowed to fiddle with the modem-router? Who's in charge?

---

### Post by SilverXill on 2009-04-02
well i know the super-user details and it's techincally my mum's but she knows nothing about internet stuff so i am allowed yes :) i'll change the channel later and see if the laptop can pick it up :)

---

### Post by coffeecat on 2009-04-02
Good luck! :wink:

---

### Post by netwarriorwy on 2009-04-02
):P Sometimes we have to get inside our modem/routers in order to fix some networking troubles...you can always try what coffeecat suggested or you can telnet it using a terminal and the same addresses suggested. Try using channels that don't interfere between themselves, in Europe these channels usually are 1, 5, 9, 13 for US is 1,6,11.
If you wanna keep the power over your modem/router try finding out the real user and password your ISP gives you to offer the Internet service, here in Peru the user is (first-letter-of-first-name)(last-name)@speedy.com.pe and the password is the first name of the internet service owner. Like [email]bcollins@speedy.com.pe[/email] pass:brad. Doing that you can play as much as you want with your modem/router and if you screw it you can always RESET it :lolflag: Find out also the original networking information that came with router...try making notes about every number or value you find in the WAN, Advanced, LAN and WLAN tabs of your configuration menu.
Remember to be very careful if you wanna try this. If you forget to put a single value after reseting, your router may not work well!
Good Luck!

---

