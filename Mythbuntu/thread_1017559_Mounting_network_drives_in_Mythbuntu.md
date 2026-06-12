---
title: "Mounting network drives in Mythbuntu"
date: 2008-12-21
forum: Mythbuntu
---

### Post by NautiusMaximus on 2008-12-21
I would like my Mythbuntu PC to be able to talk to a Windows PC on my network. I've managed to make a shared folder available on the Mythbuntu PC that the Windows PC can see, but I can't figure out how to see a shared folder on the Windows PC from the Mythbuntu PC.

I've done this before on plain Ubuntu using Nautilus, which seems to be able to cope quite nicely with network drives. But the file manager that comes with Mythbuntu doesn't seem to have this option.

What's the best way to get my Mythbuntu PC to be able to see a Windows shared folder?

I'm using Mythbuntu 8.10, and am a bit of a Linux newbie.

Thanks
NM

---

### Post by bmwman on 2008-12-21
In a Terminal type
 ```
sudo smbmount //192.168.1.XX/Shared_Folder /mnt/xp -o username=windows_username password=windows_password
```

192.168.1.XX is your IP on the XP machine, put your IP whatver it is.
/mnt/xp is where it will be  mounted.

---

### Post by NautiusMaximus on 2008-12-22
Thanks for that.

One small snag: the Windows XP machine is set up with a dynamic IP address: is there any way to avoid doing this anew each time the IP address changes?

---

### Post by false_apology on 2008-12-22
> **NautiusMaximus said:**
> Thanks for that.

One small snag: the Windows XP machine is set up with a dynamic IP address: is there any way to avoid doing this anew each time the IP address changes?

You can setup a static IP address within the TCP/IP setup in your windows machine (Just make it higher then the DHCP range reserved in your router, and set your router's IP as the default gateway and DNS server in the TCP/IP setup). Or some routers have the ability to reserve IP addresses based on a machine's MAC address. Or you can try using the name of the computer on the network instead of the IP address ( ie change //192.168.1.XX/Shared_Folder to //computer_network_name/Shared_folder )...

---

### Post by NautiusMaximus on 2008-12-24
Hm. While I could set up a static IP address, somehow it seems more satisfactory to use the computer name. Sadly, that doesn't seem to work.

When I try it, I get the following error message:

> mount error: could not find target server. TCP name computer_name/linux_share not found
No ip address specified and hostname not found

Any ideas how to solve that?

---

