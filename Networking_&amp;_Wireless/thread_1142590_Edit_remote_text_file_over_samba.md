---
title: "Edit remote text file over samba"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by benthegreat on 2009-04-29
Here's something I haven't found explained anywhere...

One thing that IS quite useful in windows is being able to open and edit a remote  text (.txt) file on another windows machine/server with notepad over HTTP. To simply punch in the IP address of a file into the open file bar and edit it is a blessing. However, for the life of me, I cannot persuade anything in ubuntu (bt4) to do this for me; gedit, vi, kate, kword, kwrite you name it iv probably tried it! I have even tried using the inbuilt wine notepad, with no success.

Because of the lack of success with a copy of notepad simulated in linux, I'm going to assume that this difficulty has nothing to do with the program being used and more to do with any limitations in samba on linux (assuming samba is used, it may not be), perhaps samba simply cannot . It could also be a security issue, notepad does not ask for a user or password to access this file as the server is set up (badly), seeing as I can edit a file without any restrictions but not access the share in the same way.

It might be the way I'm going about things, it might be the server not the client, I'm at a loss! Please could someone shed some light on the subject!

Thanks in advance,
Ben

---

### Post by uncle-c on 2009-04-29
Are you trying to edit a file which resides on a Windows machine from your Ubuntu box ? If so then make sure that you have the settings and permissions configured correctly on windows directory which holds the files i.e you can read / write and alter the files, and also that this directory is set to share. On the Ubuntu go to ----->PLACES ----> CONNECT TO SERVER and then choose SERVICE TYPE as the "Windows Share" option. It may ask for you windows login credentials and if they are correctly entered you should have access to your windows directory via Nautlius and you can double-click the txt file to edit in gedit.

---

### Post by benthegreat on 2009-04-29
Thanks for your reply

All of those are indeed valid suggestions, but do not, unfortunately apply to this situation. :(

Its not a windows share as such, simply a http server, yet the handy feature in notepad allows me to edit a simple text file over http. Quite how I do not understand, but it works. :) I'm assuming that the library in charge of dealing with files on a windows server would be samba, it may not be.

I am trying to "get at" a file from ubuntu (bt4) on a windows server. The fact I can edit the files happily in windows would suggest that permissions are not an issue. I'm not really looking for a work around as such, more a reason why nothing in linux appears to be able to do something a simple windows app achieves with ease...

thanks again
Ben

---

