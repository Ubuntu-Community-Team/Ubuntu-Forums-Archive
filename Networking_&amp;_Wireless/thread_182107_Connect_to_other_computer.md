---
title: "Connect to other computer?"
date: 2006-05-25
forum: Networking &amp; Wireless
---

### Post by Elis on 2006-05-25
Hi
Before when I used Windows I used the program WinSCP to connect to my other computer(Debian) so I could edit textfiles and change permissions and change the owner of a file and so on. So my question is how I should do it now from Ubuntu? Can I do it from Nautilus or is where another program that I could do it from?

If I in Nautilus use 'connect to server' and log in with ssh and for example root@myothercomputersipadress, and try to edit a file in texteditor(gedit) I cant change anything even though I'm root and the file is 777?

It works fine to log in with the terminal(command line) and do everything, but it would be easier to do it more graphically if its possible.

---

### Post by tribaal on 2006-05-25
I'm not sure I understand what you're looking for, but here are two way to connect to a windows machine:

- As you said, ssh. In nautilus you can browse ssh graphically by typing "ssh://user@host" in the adress bar (ctrl-l). Nautilus will prompt you for a password etc... like ssh would do.

- You can access a windows machine very easily with the terminal server client ("Applications -> Internet -> Terminal server client" under dapper). If your machine is windowsXP /NT then you want to access it with the RDPv5 protocol. You'll be shown a regular windows logon screen.

Does that answer your question?

- trib'

---

### Post by Elis on 2006-05-25
Not really, but thanks anyway.
I still can't edit a text file with gedit when I'm logging in like that using ssh in Nautilus. I can open the file, but not do anything with it. I want to be able to edit a textfile on my linux(debian) computer from my linux(ubuntu) computer.

---

### Post by tribaal on 2006-05-25
Hum... so isn't the nautilus/ssh solution working for you?

You can always try to use the command-line ssh ("ssh user@hostname"), then once the sub-sheel is open on your remote machine, you can simply cd to the diretory where your file is stored, and then use nano or vi to edit it... give you have the right to do so.

Once your ssh session is open you can always "su" and becaome root on the distant machine if you need to edit something like a config file. Remember there is no sudo on debian by default, so "su" is probably the way to go.

- trib'

---

### Post by Elis on 2006-05-25
It works fine using the command line and log in with ssh ("ssh user@hostname") and edit files with nano, but not when I'm trying to do the same thing in Nautilus. Oh well, at least I can use the commandline/nano way to edit files.
Thanks tribaal for trying to help me :)

---

