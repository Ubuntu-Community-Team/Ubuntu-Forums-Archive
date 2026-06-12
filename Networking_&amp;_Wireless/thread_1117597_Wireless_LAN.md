---
title: "Wireless LAN"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by rockingrector on 2009-04-06
Hi,
As will soon become abundantly clear, I'm a newbie.
I have two laptops running Ubuntu 8.10 and my husband has a laptop running Windows XP.
We have a wireless router and connection to the internet by all three machines is OK.
Both my Ubuntu machines can 'see' each other and can 'see' the XP machine. I can access files on the XP machine from either of the Ubuntu laptops, but I cannot access files on Ubuntu laptop 1 from Ubuntu laptop 2 and vice versa. The Ubuntu machines demand a password from each other, but when I input the password I use on bootup, it's apparently no good.
Do I have to add each machine to the other under 'System-Admin-Users and groups'? Do I need to use a different password? Do I need to change the User-ID? Or should I be doing somethign completely different?

---

### Post by superprash2003 on 2009-04-06
you would need to create a samba user for this.. read this tutorial [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by rockingrector on 2009-04-06
Thanks so much. I'll give it a whirl and let you know what transpires.

---

### Post by rockingrector on 2009-04-07
I'm stuck on Step 5 of your tutorial. when I type: gksudo gedit/etc/samba/smbusers, text editor doesn't open up with the smbusers file, just defaults back to the terminal prompt.

Not sure what to do now - can you help?

---

### Post by t0mppa on 2009-04-07
> **rockingrector said:**
> gksudo gedit/etc/samba/smbusers

That means trying to run a program called "gedit/etc/samba/smbusers" with graphical super user access. Instead what you want, is to run gedit and edit the file in the above mentioned path. So put a space inbetween and try running "gksudo gedit /etc/samba/smbusers" on your terminal.

---

### Post by rockingrector on 2009-04-07
Thanks! Won't now be at other computer until tomorow evening - but will let you know if I manage to share!
many thanks for your time and help.

---

### Post by rockingrector on 2009-04-08
Sadly, doesn't seem to work for me. Have now entered all the code and see that from a Ubuntu machine you have to type smb://(pc name or pc ip) When I do this, I get "no such file or directory" Where can I check the official pc name? Maybe I've got this wrong. The ip seems to be the same on both machines - 127.0.0.1 - or am I looking at the wrong thing here as well?
Help!!

---

### Post by t0mppa on 2009-04-08
127.0.0.1 (also called localhost) is an IP address that always loops back to the computer you are currently using.

To find your IP address in Ubuntu run this in a terminal (lists one address per each network you're in): ```
ifconfig | grep 'inet addr'
``` or open System / Administration / Network Tools and select the correct network device from the drop down.

---

### Post by superprash2003 on 2009-04-08
also there is this nautilus bug.. so try refreshing the page.. and opening it two or three times..

---

### Post by rockingrector on 2009-04-08
Still struggling, I'm afraid. When I type smb://10.0.0.17 I get 'no such file or directory.'

I presume I should type this into a terminal rather than Firefox web address bar? (Anyway, tried that and nothing at all happened!)

Don't quite understand what I should refresh in case of the nautilus bug.

Sorry guys - can you help any further?

---

### Post by wkulecz on 2009-04-08
> I have two laptops running Ubuntu 8.10 and my husband has a laptop running Windows XP.
We have a wireless router and connection to the internet by all three machines is OK.
Both my Ubuntu machines can 'see' each other and can 'see' the XP machine. I can access files on the XP machine from either of the Ubuntu laptops, but I cannot access files on Ubuntu laptop 1 from Ubuntu laptop 2 and vice versa.

By chance, is the XP machine on the wired network of the router and the Ubuntu machines on the wireless?

If so, check to see that your router does not have "AP Isolation" enabled.  Many Linksys wireless routers ship with this as default and it will prevent wireless to wireless file sharing from working!  If this is the case, you will never fix it by editing the samba config files.

---

### Post by rockingrector on 2009-04-08
No, they're all wireless. None of them plugged directly into the router.

I have Windows Vista and Ubuntu on one machine. Strangely, I can link OK to the Vista from the other Ubuntu machine, but not to Ubuntu. I've also managed to set up printing (by dint of following help!), so I presume there's just something small I'm doing wrong.

---

### Post by superprash2003 on 2009-04-09
you should type that line in places->computer .. not firefox..

---

### Post by rockingrector on 2009-04-09
Do you mean in a terminal? When I click on places -> computer, there doesn't seem to be anywhere to type it in.

---

### Post by t0mppa on 2009-04-09
Clicking the button below the navigation icons/text will switch the "address bar" thingie between typable and graphically showing each directory in your path. See the picture (I don't have default icons, but the place should be the same).

---

### Post by rockingrector on 2009-04-10
Fantastic! Why had I never noticed that?? Won't be at the other computer now until Tuesday, so will let you know then how it goes.
Thanks so much.

---

### Post by Alias1407 on 2009-04-10
Type,
smb://[ip]

into nautilus, as long as you have samba installed

---

### Post by rockingrector on 2009-04-15
Now back with the two Ubuntu machines and have typed smb://10.0.0.17 into Nautilus on this machine and get this error message:
Could not display smb://10.0.0.17.
Error: Failed to retrieve share list from server. Please select another viewer and try again.

Get the same message when I type the other address into the other machine.

Is this the Nautilus bug or have I done something else really stupid??

---

