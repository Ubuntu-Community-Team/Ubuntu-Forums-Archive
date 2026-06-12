---
title: "Do I need a static IP address to share files with Windows using Samba?"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by jcd29 on 2010-08-30
I seem to remember I could just use DHCP given addresses when sharing from Windows to Windows, and they'd keep sharing even when the IPs changed.

---

### Post by lukeiamyourfather on 2010-08-30
A static IP address is not required to share files with Samba.

---

### Post by jcd29 on 2010-08-30
> **lukeiamyourfather said:**
> A static IP address is not required to share files with Samba.

Thanks! So if my IP address changed by DHCP I'd still be able to keep sharing with the other computers like how it was with Windows?

---

### Post by lukeiamyourfather on 2010-08-30
> **jcd29 said:**
> Thanks! So if my IP address changed by DHCP I'd still be able to keep sharing with the other computers like how it was with Windows?

Yes, as long as the shares are accessed by hostname and Samba is configured properly on the server.

---

### Post by pricetech on 2010-08-30
If it makes your life easier you can have your router assign the same IP to each computer according to MAC address.

At least with most routers anyway.  Look for something like "IP Reservation" or some such wording as that.

In case host name doesn't always work.

---

### Post by jcd29 on 2010-08-30
> **lukeiamyourfather said:**
> Yes, as long as the shares are accessed by hostname and Samba is configured properly on the server.
All the important things I have to edit are in smb.conf, right?
> **pricetech said:**
> If it makes your life easier you can have your router assign the same IP to each computer according to MAC address.

At least with most routers anyway.  Look for something like "IP Reservation" or some such wording as that.

In case host name doesn't always work.
I was trying to keep the addresses dynamic for now, but yeah I could do that.

Oh another thing: should I install CIFS or smbfs? Or just samba?

---

### Post by Iowan on 2010-08-30
> **jcd29 said:**
> 
Oh another thing: should I install CIFS or smbfs? Or just samba? I've never installed **smbfs**, but have seen threads that recommend it. In reality, **smbfs** will install CIFS for you (or so I've read...)

---

### Post by jcd29 on 2010-08-30
> **Iowan said:**
> I've never installed **smbfs**, but have seen threads that recommend it. In reality, **smbfs** will install CIFS for you (or so I've read...)

What would I need it for, though?

---

### Post by redmk2 on 2010-08-30
> **jcd29 said:**
> What would I need it for, though?

The package *smbfs *it is the client side of Samba.  Samba (smbd and nmbd) is the server side.

---

### Post by pricetech on 2010-08-30
Using Synaptic, install system-config-samba which will not only install Samba, but will give you a GUI to configure it with.

That's all you need.

---

### Post by pricetech on 2010-08-30
> **jcd29 said:**
> I was trying to keep the addresses dynamic for now, but yeah I could do that.

They'll still be dynamic.  It's just that your router will always assign the "reserved" IP to the MAC of the computer it's reserved for.

If for example you have a laptop, which needs DHCP for you local hotspot, it will still work just like it always did because you're not assigning an IP to the laptop.

However, when you connect back to you home network, your laptop asks for an IP from your router and your router finds the MAC in its list and assigns the same IP again to the laptop.

Hence your laptop has the advantages of a fixed IP when your home, and a dynamic IP when you're elsewhere.

Make sense ??

---

### Post by jcd29 on 2010-08-30
After doing this it should appear under "network places" in my Windows computer right away, correct? (Where do I set the hostname so it doesn't have to be accessed by IP?)

> **pricetech said:**
> They'll still be dynamic.  It's just that your router will always assign the "reserved" IP to the MAC of the computer it's reserved for.

If for example you have a laptop, which needs DHCP for you local hotspot, it will still work just like it always did because you're not assigning an IP to the laptop.

However, when you connect back to you home network, your laptop asks for an IP from your router and your router finds the MAC in its list and assigns the same IP again to the laptop.

Hence your laptop has the advantages of a fixed IP when your home, and a dynamic IP when you're elsewhere.

Make sense ??

Ah, of course. My head's being thick today :lol:

I'll check that in my router, thanks.

---

