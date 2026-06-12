---
title: "Odd sharing problem"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by Gordonbp531 on 2011-03-01
Laptop with standard Ubuntu 10.04 desktop installed, Netbook with Ubuntu 10.04 Remix installed, both with Samba4 installed and all updates installed, both on same home (wireless) network.
I have made the Public folder on each User to be shared, with read/write permissions and guest permissions checked.
If I go to network on the Netbook I can see and open, without any prompts at all, the Public folder on the laptop. However, the Laptop, although it sees the Netbook on Network, when I click on it I get a dialog box "Opening Netbook - you can cancel this operation by clicking Cancel" and then I get the error message "Unable to mount location - failed to retrieve share list from server"
Both machines are logged on with the same user and the same password.
Why should the access be OK one way but not the other?

---

### Post by headvampyre@hotmail.co.uk on 2011-03-01
Samba4 cannot currently be browsed through the network on any OS. TO bbrowse it from linux, in nautilus goto smb://COMPUTERNAME and in windows \\COMPUTERNAME

---

### Post by Gordonbp531 on 2011-03-01
> **headvampyre@hotmail.co.uk said:**
> Samba4 cannot currently be browsed through the network on any OS. TO bbrowse it from linux, in nautilus goto smb://COMPUTERNAME and in windows \\COMPUTERNAME

Maybe not. But how do you explain the fact that I can access the shared Public folder on the laptop from the netbook with no errors or popups yet when trying to do the same from the laptop I get the errors? AFAIK both machines have EXACTLY the same software and packages installed....

---

### Post by headvampyre@hotmail.co.uk on 2011-03-01
This appears to be an smbclient error - The versions included standard in ubuntu are forever breaking for no apparent reason :( have you symlinks smbclient from samba4 into /usr/sbin ?

---

### Post by Gordonbp531 on 2011-03-01
> **headvampyre@hotmail.co.uk said:**
>  have you symlinks smbclient from samba4 into /usr/sbin ?

Now you've got me - how do I do that?

---

### Post by headvampyre@hotmail.co.uk on 2011-03-02
go to terminal and type:

sudo ln -s /usr/local/samba/bin/* /usr/sbin

this should work - it did for me :)

---

### Post by Gordonbp531 on 2011-03-03
> **headvampyre@hotmail.co.uk said:**
> go to terminal and type:

sudo ln -s /usr/local/samba/bin/* /usr/sbin

this should work - it did for me :)

Nope - still the same error

---

### Post by headvampyre@hotmail.co.uk on 2011-03-03
Hmm :/ Did you compile Samba4 from source? I find that a lot of builds can be broken for no apparent reason :( I've just notcied i get this error when browsing "Windows Network", it must be a bug :( for now - just use smb://YourComputerName (after using CTRL+L to open the nautilus location box), i find this works fine for me :)

---

### Post by Gordonbp531 on 2011-03-03
> **headvampyre@hotmail.co.uk said:**
> Hmm :/ Did you compile Samba4 from source? I find that a lot of builds can be broken for no apparent reason :( I've just notcied i get this error when browsing "Windows Network", it must be a bug :( for now - just use smb://YourComputerName (after using CTRL+L to open the nautilus location box), i find this works fine for me :)

I actually uninstalled Samba 4 and re-installed Samba from the Ubuntu Software Centre, tried the "smb" location in nautilus and got "Error: Failed to retrieve share list from server
Please select another viewer and try again." AGAIN......

---

