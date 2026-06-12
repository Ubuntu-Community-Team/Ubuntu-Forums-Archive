---
title: "Cannot click &quot;apply&quot; button when entering static IP"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by Uturi on 2010-06-15
I just installed Ubuntu using WUI. It went OK. I am able to launch it, etc.

However I cannot manually enter my static IP information. I go to Edit Connections > IP4 settings > I then change the tab from DHCP to manual and then the "apply" button turns to a light darkish color and is non-selectable.

I also cannot save any network config note using gedit. It says I don't have permissions. I checked and changed my account type to Administrator and checked all the boxes then rebooted and still nothing. 

Help please.

---

### Post by Uturi on 2010-06-15
Anyone?

---

### Post by Iowan on 2010-06-15
Once/day is usually adequate for thread bumping... 
I remember it being a little tricky to get information entered for manual network configuration in Network Manager - you might need to [ENTER] the information before you can [Apply] it. To use **gedit** to edit network configuration (*/etc/network/interfaces*?), you'll need to start it with gksudo (gksu?) - either from terminal or ALT-F2.

---

### Post by Uturi on 2010-06-15
I apologize for bumping so quickly. Just irritated because I can't even get internet on it yet.. pointless for me to try it.

Regardless, I did [ENTER] the information. IP, netmask, gateway. Still the [APPLY] button never highlighted so I can click it. I went into the ROUTES settings and once I started typing in config info, the OK button became dis-selected. So I cannot "save" my IP info.

Is this a user/permissions problem? I created a new user and made sure it had admin powers.

Dunno where to go to next.

---

### Post by dineshs on 2010-06-16
> **Iowan said:**
> 
I remember it being a little tricky to get information entered for manual network configuration in Network Manager - you might need to [ENTER] the information before you can [Apply] it. To use **gedit** to edit network configuration (*/etc/network/interfaces*?), you'll need to start it with gksudo (gksu?) - either from terminal or ALT-F2.
Pl follow this step by step.
[COLOR="Blue"](Note :The IP addresses are examples.Substitute your values)[/COLOR]
click on the NM icon(on top right of the panel) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit
select ipv4 
method-manual 
address [COLOR="Blue"]192.168.1.100 [/COLOR]
mask [COLOR="Blue"]255.255.255.0 [/COLOR]
gateway [COLOR="Blue"]192.168.1.1[/COLOR] [COLOR="Red"]then hit enter [/COLOR]
DNS [COLOR="Blue"]4.2.2.1,8.8.8.8[/COLOR]
then click apply
note:You may substitute your values for IP DNS gateway etc

---

### Post by sarathps on 2011-05-13
> **dineshs said:**
> Pl follow this step by step.
[COLOR=Blue](Note :The IP addresses are examples.Substitute your values)[/COLOR]
Right-click on the NM icon(on top right of the panel) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit
select ipv4 
method-manual 
address [COLOR=Blue]192.168.1.100 [/COLOR]
mask [COLOR=Blue]255.255.255.0 [/COLOR]
gateway [COLOR=Blue]192.168.1.1[/COLOR] [COLOR=Red]then hit enter [/COLOR]
DNS [COLOR=Blue]4.2.2.1,8.8.8.8[/COLOR]
then click apply
note:You may substitute your values for IP DNS gateway etc


thanks itz working

---

