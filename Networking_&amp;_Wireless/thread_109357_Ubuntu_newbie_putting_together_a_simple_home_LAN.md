---
title: "Ubuntu newbie putting together a simple home LAN"
date: 2005-12-28
forum: Networking &amp; Wireless
---

### Post by athena on 2005-12-28
Dear Friends, 
I know very little about networking and Ubuntu, but I have an old PC with Ubuntu installed on it, and I want to do some simple file sharing with a Mac G4 running OSX.  I have found several good instructions for how to do this, but am still running into problems, and I do not think there is anything wrong with the hardware.  I just don't know what I am doing.  So is there someone here who does know how to do this, and who would be willing to walk me through the set up via instant messanger, or even by  phone. ( as long as you are in the US)  If so, I would really appreciate it.  thanks

---

### Post by mips on 2005-12-28
Please elaborate as to what you have done so far. Harware used between computers, software installed on OSX & Kububuntu, where you are hitting snags etc....Please be specific.

---

### Post by ingo on 2005-12-28
wow, you are asking a lot! All I can tell you is that you should get into samba - it enables you to link up linux, win & osx boxes. Works a treat with suse, haven't tried with (K)Ubuntu though...

---

### Post by athena on 2005-12-30
Well first of all, I can't figure out how to set up Samba on my Mac.  Can this be done? (When I downloaded Samba from the internet, I could not get a installation package, just a bunch of ISO's, which I don't know how to use) I am pretty sure it is installed on the Ubuntu system, but I can't tell because it doesn't show up as an application.  (I can set up a shared folder using SMB) If not Samba on the Mac, than how do I set up the Mac?   The ubuntu set up was farely simple.  I just installed Samba and set up a shared folder, but that is as far as I have gotten.  

I did find a post at linuxquestions.org that explained the set up, but when it got to the part where I was to verify the connection to the same network as the Ubuntu box, I get stuck.  It shows the ethernet as active, but not connected.  Is this because it doesn't know how to talk to Samba on the Ubuntu machine?  

Here is the URL for the post at linuxquestions.org, if anyone wants to look it over.  
[http://www.linuxquestions.org/linux/answers/Networking/File_sharing_with_OS_X_using_Ubuntu_5_04](http://www.linuxquestions.org/linux/answers/Networking/File_sharing_with_OS_X_using_Ubuntu_5_04)

---

### Post by kaamos on 2005-12-30
I thought samba was preinstalled in OSX? :???:
Here is a link to apples pages in any case [http://www.apple.com/downloads/macosx/unix_open_source/samba.html](http://www.apple.com/downloads/macosx/unix_open_source/samba.html)

---

### Post by athena on 2005-12-30
Probably is.  I just have no idea how to use it, except that I would imagine you do so by way of terminal.  thanks for the link

---

### Post by kaamos on 2005-12-30
What I meant was that I thought that samba is installed by default with osx, and thus is is possible just to click "connect to server" (can't remember what that was with a mac..) or something similiar, and connect to a windows share. So if your ubuntu is properly running samba, you should be able to connect to it without installing anything in osx.

Been two years since I used a mac so I might be wrong as well..
EDIT: this is what is mean
[IMG]http://homepage.mac.com/car1son/conx2server_gomenu.jpg[/IMG]

I tried networking with samba with two windows machines some time ago, and it always seemed to work as randomly as the shares in the xp machines did.. Somethimes it was accessible and sometimes not. And sometimes the shared folders on xps were accessible in ubuntu and sometimes not. Gave up and started using ssh when I needed to connect to ubuntu from windows.. :(

---

### Post by athena on 2005-12-30
there is no windows share option when you go to connect to server.  In fact, all you can do is connect to an open office ftp thingy, which is odd because that is not something I have ever used or set up.  Open office just seems to have done it all by itself.

---

### Post by kaamos on 2005-12-30
Try the ip address of the ubuntu machine to the connect to server box.

Like this:
> 
192.168.X.XX
or
> smb://192.168.X.XX/name_of_shared_folder

You can find out the ip in ubuntu with the command "ifconfig".

---

### Post by davidsrsb on 2005-12-30
Since when did openoffice have anything to do with ftp? Konqueror maybe?

---

### Post by ingo on 2005-12-30
@ athena - sorry, I don't really know a lot about OSX. However, you could install the samba server on your linux box (you probably only got the client version installed at the mo) and use SWAT - a browser tool which allows you configure samba rather than poking around the smb.config. Again, you'd have to install SWAT.

HTH

---

