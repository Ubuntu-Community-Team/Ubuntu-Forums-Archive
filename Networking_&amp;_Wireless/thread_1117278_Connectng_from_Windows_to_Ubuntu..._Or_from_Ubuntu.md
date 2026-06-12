---
title: "Connectng from Windows to Ubuntu... Or from Ubuntu to Vista"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by Ceiling Fan Man on 2009-04-05
I've got a large quantity of files on my Ubuntu box (Intrepid Ibex 8.10, 32-bit), that I need to transfer directly to a machine running Windows Vista (Ultimate, 64-bit). I can't connect to the Vista machine from Ubuntu ("Failed to retrieve share list from server") like I can to other computers on the network running WinXP Pro. So after a couple hours of trying to fight that, I thought I would just connect to Ubuntu from the Vista machine and copy them that way. That doesn't work either, because when I try to connect to the Ubuntu box from Vista, it wants me to log in with username and password. My user/pass for Ubuntu does not work here, and everything I've looked up to setup this user/pass has not worked.

I need at least one to connect to the other and I would be happy... But it would be ideal if I could make them connect to each other both directions. Thanks.

    -Ceiling Fan Man

---

### Post by Cybie257 on 2009-04-05
I had that exact same problem last night. I ended up going into Synaptics Package Manager and reinstalled all the SAMBA packages I could find with the search "samba". After that, I was able to share the folders and everything worked. I'm thinking an update broke something. Give that a try and see if that fixes things.

Also, be sure to add yourself to the samba share..

IE: sudo smbpasswd -a <your username>

Then you should be able to connect from Vista to Ubuntu. No guarantees, though, as I refuse to use Vista because it's networking abilities are so broken down compared to XP. At least in my few experiences experimenting with Vista.

-Cybie

---

### Post by Ceiling Fan Man on 2009-04-05
[QUOTE=Cybie257]IE: sudo smbpasswd -a <your username>

Then you should be able to connect from Vista to Ubuntu. No guarantees, though, as I refuse to use Vista because it's networking abilities are so broken down compared to XP. At least in my few experiences experimenting with Vista.[/QUOTE]

Thank you! That terminal command actually worked... Nothing I could find by Googling would. I can now connect to the Ubuntu machine from Vista.

And yes... Vista has lots of problems... I'm working on a customer's computer though, and you know... They're ALWAYS right. :lol:

I'm still unable to connect to the Vista machine from Ubuntu, but that's okay. I'd say this is as solved as it needs to be. :)

---

