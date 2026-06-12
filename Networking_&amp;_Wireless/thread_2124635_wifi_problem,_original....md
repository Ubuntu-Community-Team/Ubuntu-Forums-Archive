---
title: "wifi problem, original..."
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by BradJF on 2013-03-11
iv installed ubuntu twice now as the first time i gave up on getting it to work as it wouldnt connect to the internet.
im no computer expert so you may have to explain in simple turms
so the problem:
i have a built in wireless card which i press f12 to activate and then the light turns from orange to white.
this does not work on ubuntu as i believe i need to install a driver.
the problem is my laptop is not a supported linux device so im surching for drivers.
i believe i found one which contains a lot of things including a folder called driver and a .tar.gz folder(which i think you can install?)
i cant activate the wifi card while in linux just windows.
can anybody help? direct me to a tutorial? make a tutorial?
i just really want my linux eviroment to work as i believe i can make more use out of its next to limitless restrictions than i can windows.

so my laptop is a compaq presario cq57 355sa which uses the cq 356sa drivers. [http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=5177006&lang=en&cc=us&taskId=135&prodClassId=-1&prodTypeId=321957&prodSeriesId=5145720](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=5177006&lang=en&cc=us&taskId=135&prodClassId=-1&prodTypeId=321957&prodSeriesId=5145720)
im running windows 7 dual booting with ubuntu 12.10 both 64bit
wifi card is: [[SIZE=2][COLOR=#003366]Realtek RTL8188CE 802.11b/g/n[/COLOR][/SIZE]]("http://ubuntuforums.org/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=5145720&prodNameId=5177006&swEnvOID=4063&swLang=13&mode=2&taskId=135&swItem=ob-105197-1")
please somebody help im on my last straw.
i believe i can get the driver from here [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=272&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=272&DownTypeID=3&GetDown=false&Downloads=true)
but im unable to install it.
please help

feel free to email me on [EMAIL="bradfullwood@hotmail.com"]bradfullwood@hotmail.com[/EMAIL]

---

### Post by ajgreeny on 2013-03-11
You should not give your email address in posts such as this as you may lay yourself open to masses of spam.  I suggest you edit your post and remove it.  Also remember that it is not good policy to ask for private answers by email as it takes away one of the main objectives of the whole forum, ie to offer searchable answers to problems.

However to answer your question, the archive you downloaded from that link will be extractable to a folder with the same name and that folder contains a file called **install.sh.**  Make that shell script executable either with command chmod +x path/to/install.sh or using a right click in nautilus ->Properties.  You should then run the shell script from that folder by double clicking and selecting "Run in terminal" or with the command ./install.sh from the folder it is in.  I am not sure if the script will ask you to run as root, or if you will need to run it from then start with sudo so try first as your normal user.

---

### Post by aaron3uk on 2013-03-12
ahhhhhh im having the excalt same problem ,i have the same wireless card and cant get to the internet, 

I have downloaded the correct driver onto a usb but just need to know how to install it, can you please explain how to install this file,  you said chmod +x path/to/install.sh
but do i need to change any of the text? the file is on my desktop please explain as basic as possible how to extract,install or what ever it is to get this file in the system :( :(

---

### Post by ajgreeny on 2013-03-12
I used the "path/to/install.sh" as I had no idea where you had put the extracted archive.  As it's on your desktop the path would be **/home/$USER/Desktop/<name-of-rtl-folder>/install.sh** but it is probably easiest to simply right click on the install.sh file and in the Properties ->Permissions tab make sure it is executable.

Now double click on it and choose "Run in terminal".  That may be all that is needed, though as I said, I do not know if it expects to start as root or if the terminal will ask you for a password at some point in the installation.

---

