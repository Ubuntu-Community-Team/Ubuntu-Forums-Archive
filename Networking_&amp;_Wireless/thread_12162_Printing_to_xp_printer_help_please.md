---
title: "Printing to xp printer help please"
date: 2005-01-22
forum: Networking &amp; Wireless
---

### Post by philip41 on 2005-01-22
Is at all possible to get Ubuntu to use the Hp photosmart 7260 usb printer that is installed on my xp pro pc.
I have the network all setup and both pc's can see each other.
The 2 other pc's (both xp) can see and use the printer. 

As far as i can tell from all the extensive searchs here and Google i have set up correctly, however i cannot even print a test page.

Under printer properties, it is setup as Network printer( windows printer(smb) host is the brain (the pc the printer is connected to), Printer (printer) the name of the printer on the-brain.
User name and password are that used on the-brain.
The driver on Ubuntu is hpijs.

The status always reads : Connection failed with error NT_STATUS_UNSUCCESSFUL.

I am running Hoary with all updates installed.

As i said i have made good use of the Search button and tried most if not all the suggestions available.

If some one has got Ubuntu using an xp installed printer, please let me no how.

thanks

 phil.

---

### Post by macewan on 2005-01-22
[QUOTE=philip41]Is at all possible to get Ubuntu to use the Hp photosmart 7260 usb printer that is installed on my xp pro pc.
I have the network all setup and both pc's can see each other.
The 2 other pc's (both xp) can see and use the printer. 

As far as i can tell from all the extensive searchs here and Google i have set up correctly, however i cannot even print a test page.

Under printer properties, it is setup as Network printer( windows printer(smb) host is the brain (the pc the printer is connected to), Printer (printer) the name of the printer on the-brain.
User name and password are that used on the-brain.
The driver on Ubuntu is hpijs.

The status always reads : Connection failed with error NT_STATUS_UNSUCCESSFUL.

I am running Hoary with all updates installed.

As i said i have made good use of the Search button and tried most if not all the suggestions available.

If some one has got Ubuntu using an xp installed printer, please let me no how.

thanks

 phil.[/QUOTE]


This [linuxprinting.org article](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7260) may assist.

There is a [Source Forge Project](http://hpinkjet.sourceforge.net/) and finally the HPIJS 1.6 driver is being recommended at [this](http://www.linuxprinting.org/pipermail/general-list/2004q2/005342.html)  thread.

---

### Post by Buffalo Soldier on 2005-01-22
[QUOTE=philip41]The status always reads : Connection failed with error NT_STATUS_UNSUCCESSFUL.

If some one has got Ubuntu using an xp installed printer, please let me no how.
[/QUOTE]

Experienced the same error message before. What I did after that was enabled the Guest User account in Windows XP.

---

### Post by philip41 on 2005-01-22
Thanks guys i will give both a go, i will go for the driver first.

---

### Post by philip41 on 2005-01-22
This is driving me Nuts, i get to step 6) type the command exactly as written, hit enter, after some checking, a configure error is returned. "Configure: Error: no acceptable C compiler was found"  

1.  Download the HPLIP tar file that contains the current HP printing software from [http://hpinkjet.sourceforge.net](http://hpinkjet.sourceforge.net).
      Suggestion: Note the folder in which you saved the HPLIP tar file.
   2. Open a console window.
   3. Enter this command to navigate to the folder that contains the HPLIP tar file that you downloaded in step 1:
      $ cd [file path] (for example: $cd /home/documents)
   4. Enter this command to extract the driver files from the HPLIP tar file:
      $ tar xvfz [HPLIP filename.tar.gz] (for example: $ tar xvfz hplip-0.8.tar.gz)
      The files are extracted to a folder named for the HPLIP version (for example, "hplip-0.8").
   5. Enter this command to navigate to the directory containing the HPLIP files:
      $ cd [folder name] (for example: $ cd hplip-0.8)
   6. Enter this command to configure the computer for the driver:
      $./configure --prefix=/usr
   7. Enter this command:
      $ make
   8. Follow these steps to log in as the super user:
         1. Enter su.
         2. Press Enter.
         3. Enter the root password.
            Note: The root password gives you administrative privileges on the system.
         4. Press Enter.
   9. Enter this command:
      # make install
  10. Enter this command:
      # /etc/init.d/hplip restart

After installing the printer software, follow these steps to add the printer.

---

### Post by philip41 on 2005-01-23
Anybody.

---

### Post by Buffalo Soldier on 2005-01-23
[QUOTE=philip41]This is driving me Nuts, i get to step 6) type the command exactly as written, hit enter, after some checking, a configure error is returned. "Configure: Error: no acceptable C compiler was found" [/QUOTE]You're compiling a driver for your printer? The aren't any default driver for your printer in Ubuntu? Anyway, to solve that error, I'd suggest:```
sudo apt-get install build-essential
```

---

### Post by philip41 on 2005-01-24
[QUOTE=Buffalo Soldier]You're compiling a driver for your printer?[/quote]

I have Downloaded the driver from the HP site.

> 
 The aren't any default driver for your printer in Ubuntu? 

Thats why i DL from HP.
> 
Anyway, to solve that error, I'd suggest:```
sudo apt-get install build-essential
```

I take it i start the above install again.

Thanks for  your help.

---

### Post by macewan on 2005-01-24
did it work?

---

### Post by philip41 on 2005-01-25
[QUOTE=macewan]did it work?[/QUOTE]

Not as yet

---

### Post by stream on 2005-03-04
hi philip41,

I have managed to get this printer working using packages from ubuntu and universe, there should be no need to compile anything at all ... trick is that this printer does not work with kernel printer module. It needs hpoj driver.
here is how i've done it:

1) apt-get install hpoj
   postintstall script will find your printer
2) /etc/init.d/cupsys restart
3) Now go to computer -> sys conf -> printing -> add new printer
   choose 'ht photosmart 7200 series' not the other one
   next steps are easy ...

hope it helped, good luck

---

