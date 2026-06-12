---
title: "Wi-FI Protected Setup supported?"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by Desabrir on 2010-05-04
Heyas,

So windows has a feature to automatically connect to a Wifi protected router with the click of a mouse and a push of a button on the router. Is this feature supported in any of the distros? It seems that the network applet doesn't have the click of the mouse type feature that windows has as it just asks for the password with no other options.

thanks,

desabrir

---

### Post by lores on 2010-08-01
So, any user-friendly support for WPS?

---

### Post by Desabrir on 2010-10-01
I think near 6 mos is an appropriate span of time for a bump. 


Bump!

---

### Post by grahammechanical on 2010-10-01
My wireless connects automatically when I boot up. Actually I am using ethernet but I know Wireless does connect automatically. Right click the network icon >edit connections, select your wireless connection, enter your logon password and check (tick) connect automatically. If you have already put the wireless key into the settings then it should work even without a mouse click. If you want to do it manually, then left click the network icon and select the wireless network  to connect to. If it is your wireless network (modem/router) and the wireless key or password is already in place then network manager will search for the network and connect with just two mouse clicks. 

Regards.

---

### Post by lores on 2010-10-01
@grahammechanical, the problem is NetworkManager doesn't support specifically WPS. It's something else than typing the wireless key manually - v. OP.

So, any hope?

---

### Post by Desabrir on 2010-10-01
I don't have a problem automatically connecting to unsecured and secured WIFI. WPS is a system where you press a button on the router and it gives access to a requesting PC without having to divulge the key. A lot easier than entering a key and much faster. I'm sure it is a lot more technical than that, but for the end user thats it.


The reason I'm asking about this is at one of the stations at work we have a wireless router that has the WPS button on it. All the other stations are wired. We're allowed access to it for internet but the admin won't give us the key and told us we have to use the WPS feature. I was the only one who knew what he was talking about. Maybe I'll just tell him I have linux.

Maybe I'll go to the network manager project site and see what I can dig up. Not sure why I didn't think of that 6 mos ago.

h4n5

---

### Post by lores on 2010-10-01
Just one remark: on Windblows, connecting to a WLAN using WPS seems to give you access to the wireless key (you can preview it in the built-in netman).

---

### Post by Desabrir on 2010-10-01
I found very little information and nothing at the gnome networkmanager project. It appears that WPS is supported in the WPA supplicant, but I have no idea how to enable it or if NetworkManager even supports it. :(

Also, I have no way to test it as my router here at home does't support WPS

[http://svn.dd-wrt.com:8000/dd-wrt/browser/src/router/hostapd-wps/wpa_supplicant/README-WPS?rev=14736]("http://svn.dd-wrt.com:8000/dd-wrt/browser/src/router/hostapd-wps/wpa_supplicant/README-WPS?rev=14736")

adam

---

### Post by Desabrir on 2010-10-01
> **lores said:**
> Just one remark: on Windblows, connecting to a WLAN using WPS seems to give you access to the wireless key (you can preview it in the built-in netman).

Didn't know that. I've ditched windows back in may or so when I sold my other laptop. My netbook with UNR is my only CPU.

---

### Post by grahammechanical on 2010-10-01
Hi Desabrir

As you have found out, if I was working for your employer I would not know what the Admin was talking about either. Thanks for explaining. The redness is going out of my face a little bit. I have learnt something.

regards.

---

### Post by grahammechanical on 2010-10-01
Stung by my ignorance I have been doing some research. WPS = WiFi Protected Setup. You want to use the PBC (Push Button Configuration) method of connecting.

You might want to check out this utility:

[http://sourceforge.net/projects/wpsd](http://sourceforge.net/projects/wpsd)

or

[http://wpsd.sourceforge.net](http://wpsd.sourceforge.net)

I found some information that says: "New wpa-cli commands wps_pin and wps_pbc are used to manage WPS negotiation."

Test at your own risk. 

regards.

---

### Post by Desabrir on 2010-10-01
Ahh! Thank you very much Graham! Unfortunately i have no way to test it, but I'll d/l the tarball and save it until I'm back at that particular station.

D

---

### Post by grahammechanical on 2010-10-02
Hi Desabrir

Since my last post I have been thinking about what I have learnt about WiFi Protected Setup. I think the developers of Ubuntu should seriously consider making it easy to implement, especially for laptop and netbook installations.

Retail outlets that provide free access to WiFi should be using WPS. I have never tried to use wireless in one of these places. No laptop. An unsecured wireless network is not only easy to connect to for anyone with a wireless enabled computer, but anyone can "listen-in" on the transmissions. The wireless communication between a customers wireless device and the retail outlet's wireless access point is unsecure.

WPS is a way of allowing the wireless access point and the customer's wireless device to connect and exchange the pass-phrase that allows encrypted communication without physically giving out the pass-phrase. I think that this method of connecting to a free wireless network will become more widespread. Operating systems will need to provide this service in a seamless way .

In defence of Linux, in my search for information I noticed several remarks about WPS being made easier in Windows 7. This means that it was not so easy in Vista.

I wonder if your system admin understands what WPS really is? Or does he/she go by the simple rule, "you only connect if I press this button?" I like to understand how things work not just what to do to get them to work.

Have fun. Regards

---

### Post by Desabrir on 2010-10-02
I had vista on my windows laptop, WPS worked fine on it.

---

### Post by tehowe on 2012-03-15
> **Desabrir said:**
> Heyas,

So windows has a feature to automatically connect to a Wifi protected router with the click of a mouse and a push of a button on the router. Is this feature supported in any of the distros? It seems that the network applet doesn't have the click of the mouse type feature that windows has as it just asks for the password with no other options.

thanks,

desabrir

Still no WPS in Precise. It's long become standard functionality for wireless devi8es.

---

### Post by lores on 2012-03-15
> **tehowe said:**
> Still no WPS in Precise. It's long become standard functionality for wireless devi8es.

Does anyone know how to implement this feature? What are the main obstacles? Is there any project underway?

---

