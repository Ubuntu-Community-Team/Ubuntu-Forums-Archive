---
title: "Help needed with ndiswrapper"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by 30857 on 2009-02-09
Hello, I am using ubuntu 8.10.

I am currently reading the ubuntu help guide found on this address: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The problem is just under 2.2.2 i need to (quote from page) 
Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order:

    *

        sudo dpkg -i ndiswrapper-utils_*.deb

        sudo dpkg -i ndisgtk_*.deb

<!> The commands listed above are a general example of how to install a .deb package from the command line. You need to be in the directory where the files were copied to. 

How do i find out where these were copied too and can someone give me the basic command if possible (complete beginner talk please ;)?

---

### Post by Sam Lars on 2009-02-09
The files will be wherever you saved them.  When you open a new terminal from the menu, I think it starts in your home directory.  You can do
```
cd Desktop
```
to get to your desktop, etc.  You can do
```
ls
```
to see if the files are there.  If they are, you can run those commands.

---

### Post by 30857 on 2009-02-09
When i downloaded the 3 packages and installed them from earlier in the other web page, i saved them to desktop.

But, when i do "cd desktop" and "ls" the files that are saved to the desktop do not show up(ndiswrapper-common_1.52-1ubuntu1_all.deb, ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb, ndisgtk_0.8.4-1_i386.deb)

Any further help please?

---

### Post by Sam Lars on 2009-02-09
When you open a terminal, it will start in your home directory and look like this:
```
user@computer:~$
```
The ~ points to your home directory.
When you run
```
cd Desktop
```
it's case sensitive, the D has to be capitalized.  It should then say
```
user@computer:~/Desktop$
```
The ls command should then show you everything you have on your desktop.  If you run your
```
sudo dpkg -i
```
command, you can type
```
sudo dpkg -i ndis
```
and then press Tab to fill the name with any files starting with "ndis" in the current folder.  Pressing Tab twice will show you all possibilities if there is more than one.

---

