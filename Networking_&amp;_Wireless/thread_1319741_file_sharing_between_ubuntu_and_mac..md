---
title: "file sharing between ubuntu and mac."
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by josephcohen on 2009-11-08
So I used smb to easily make a shared folder on ubuntu that I could access from my mac but now I want to do it the other way round. I did one way by turning on remote login and then in ubuntu using connect to server by ssh. the only problem is that it shows ALL of the files on my mac. From the root. What I really want to do is be able to only share the shared folder on my mac. 

btw, Im using ubuntu 9.10 and my mac is running leopord. and of course they are both on the same network.

Id like to use smb so I could be using the same form of file sharing both ways. 

thanks :)

---

### Post by josephcohen on 2009-11-09
Ok so I tried going places, connect to server, Windows share then I put the mac's local ip address in the server field and the shared folder name in the folder field. But it didnt work. anyone had experience with that?

---

### Post by josephcohen on 2009-11-11
Or could I just use the same folder on each side?

---

### Post by josephcohen on 2009-11-14
I keep googling and trying but I cant get it to work. any help?

---

### Post by driftertx on 2009-11-14
If you don't care about the interface, you could do: 

'sudo apt-get install openssh-server'

then use any variety of ssh interface from your mac to copy the files over. 

Username = ubuntu username
Password = ubuntu password

---

### Post by coffeecat on 2009-11-14
> **josephcohen said:**
> any help?

Setting up a Windows/smb share in MacOS to be seen in Ubuntu isn't difficult but I've found a couple of wrinkles. This is in Snow Leopard, but it should be good for Leopard.

Go to System Preferences > Internet and Wireless > Sharing. Add whatever folders you want to share and tick 'File Sharing'. Adjust the permissions under 'Users' to whatever is best for you. The default is to set up afp sharing, so click on the 'Options' button and tick the Windows/SMB tickbox. Untick afp if you want. Click on 'Done' and that's it. Before you quit System preferences, make a note of the Mac hostname which is shown under 'Computer Name'. Mine is 'Macintosh.local' which I guess is the default, but you can change this with the 'Edit' button.

From here on once we get into Ubuntu your mileage may vary because I found Jaunty needed a bit of tinkering to work without issue with smb shares, but Karmic seems better behaved. Anyway, this is my Karmic experience.

In Karmic: Places > Network - my Mac shows up with its own icon labelled '*MyName('s)* Computer'. If I double-click on that I get 'smb://macintosh.local/' in the address bar of the Nautilus browser, but nothing showing in the window. But if I add the share folder name to the address bar ('smb://macintosh.local/*sharefoldername*/') I get access to the contents of the Mac folder on my Ubuntu desktop.

---

### Post by josephcohen on 2009-11-16
> **coffeecat said:**
> Setting up a Windows/smb share in MacOS to be seen in Ubuntu isn't difficult but I've found a couple of wrinkles. This is in Snow Leopard, but it should be good for Leopard.

Go to System Preferences > Internet and Wireless > Sharing. Add whatever folders you want to share and tick 'File Sharing'. Adjust the permissions under 'Users' to whatever is best for you. The default is to set up afp sharing, so click on the 'Options' button and tick the Windows/SMB tickbox. Untick afp if you want. Click on 'Done' and that's it. Before you quit System preferences, make a note of the Mac hostname which is shown under 'Computer Name'. Mine is 'Macintosh.local' which I guess is the default, but you can change this with the 'Edit' button.

From here on once we get into Ubuntu your mileage may vary because I found Jaunty needed a bit of tinkering to work without issue with smb shares, but Karmic seems better behaved. Anyway, this is my Karmic experience.

In Karmic: Places > Network - my Mac shows up with its own icon labelled '*MyName('s)* Computer'. If I double-click on that I get 'smb://macintosh.local/' in the address bar of the Nautilus browser, but nothing showing in the window. But if I add the share folder name to the address bar ('smb://macintosh.local/*sharefoldername*/') I get access to the contents of the Mac folder on my Ubuntu desktop.

O! thank you very much! this makes more sense now. But, how can I make a shared folder? and where does it have to be? in the root? I thought the only shared folder is the "public" folder which is in the user folder in some other folder...

---

### Post by coffeecat on 2009-11-16
> **josephcohen said:**
> But, how can I make a shared folder?

Um - I thought I explained that bit. :-s Using System Preferences (in the Mac).  

> **josephcohen said:**
>  and where does it have to be?

Anywhere in your home folder.

> **josephcohen said:**
>  in the root?

Not a good idea.

> **josephcohen said:**
> I thought the only shared folder is the "public" folder which is in the user folder in some other folder...

"In the user folder in some other folder." :-k Hmmm. I have a 'Public' folder in my home folder, but you don't have to use that if you don't want to.

---

### Post by bcl1966 on 2011-10-27
This is an old thread, but as it's still open and I was looking for the same information, I thought I'd share an alternative, and what I think is a simpler method.

I had a hell of a time trying to get sharing working between OSX 10.7 and Ubuntu 11.10 using samba and stumbled across netatalk.

Installed it, restarted the service and away I went. It's highly customizable but straight out of the box it makes your home directory accessible on the mac.


[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume).

---

### Post by nothingspecial on 2011-10-27
Thank you for your input but old threads must be laid to rest.

Closed.

---

