---
title: "Wireless Adapter"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by aviator1 on 2010-10-16
I'm new to Ubuntu. Just installed 10.04. 
 
Can anyone recommend an "out of the box" wireless adapter?
 
I have a WUSB300N coonected, and it works fine in Vista.
 
I have read the links on this forum regarding how to get it working, but they are a bit complicated for me.
 
Any help would be appreciated.
 
Regards to All,
 
Dave

---

### Post by bkratz on 2010-10-16
See this one? It looks pretty easy to follow. See posts 6 and 9 ( 9 modifies 6). If you need help post where you had a problem.

[http://ubuntuforums.org/showthread.php?t=873027](http://ubuntuforums.org/showthread.php?t=873027)

---

### Post by aviator1 on 2010-10-16
Thanks for your response. I have seen the info from that link.
 
I just don't understand where to put that code into what file.
 
I opened "terminal" and was able to do some basic looking around.
 
I downloaded ndiswrapper, and have it in a file on my HD. I don't know how to "unwrap" it, nor do I know what a tar file is. I have also downloaded the wusb300n.tar file.
 
As an example, how would I "Extract them to /opt/ndis/:
# mkdir /opt/ndis
# tar xvf WUSB300N.tar C
/opt/ndis/"
 
It's been a long time since I have used dos type statements.
 
I really appreciate your response.
 
Dave

---

### Post by bkratz on 2010-10-16
Posts 6 and 9 describe using the Windows drivers supplied with the device. If you still have the disk you wouldn't have to extract anything simply use "windows wireless drivers" under system>>administration and install the windows driver there.

---

### Post by johnnytm on 2010-10-16
[LEFT]When it comes to tar files they are really not as complicated as you think. but one way to make things way easier is to install terminal in nautilus. This eliminates the need for constantly having to change directories through terminal and the commands can be run from the folder itself. To do that open terminal and enter this
```
 
sudo add-apt-repository ppa:flozz/flozz
sudo apt-get update
sudo apt-get install nautilus-terminal

```then restart nautilus 
```

nautilus -q && nautilus & exit

```Then browse to where the tar the file is located, right click on it and press extract here, open the new folder that appears, named the same as the tar file, locate the readme file located in there, open that and enter the terminal commands, that come later than the cd or change directory  commands right in the terminal windows that is open in your folder.
[/LEFT]

---

### Post by aviator1 on 2010-10-19
Johnny:
 
Thanks. That clears up a bunch.

---

### Post by TBABill on 2010-10-19
Intel and Realtek chipsets for wireless seem to have pretty good luck out of the box. However, in 10.10 my Realtek isn't working but my Broadcom is. Problem with Broadcom is it requires you to install the driver after installing the OS so you do have to take an extra step or two to get it going. (Plug into the router, download updates and install the proprietary driver suggested under System>Administration>Hardware). For Intel and Realtek those steps are not necessary from my own experience with them both.

---

