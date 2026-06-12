---
title: "Xsane Trouble"
date: 2017-01-05
forum: Multimedia Software
---

### Post by shane_faulkinbury2 on 2017-01-05
I'm able to scan images scanned from my Brother MFC-J475DW using xsane however it saves the images as root and I'm unable to view them.  I need to send the UPC of something I bought to the    	 	 	 	     	 	 	 	 manufacturer so they need to be able to view it.  How do I accomplish this?

---

### Post by #&amp;thj^% on 2017-01-05
Your not using xsane as root are you?
This might be worth a shot no guaranties it will solve this...but maybe add you self to the scanner users group:

```
sudo usermod -a -G scanner <yourusernamehere>
```

---

### Post by shane_faulkinbury2 on 2017-01-05
Well that didn't work because now all I can do is get a preview!  The attached screen shots are when I fire it up it wants me to be root, running it as a regular user and me trying to scan it as root!

---

### Post by #&amp;thj^% on 2017-01-06
Not sure what to offer here...but running it as root is no go (Taboo) for me.
Adding yourself to the scanner Group should have solved that...with a good and proper installation of Xsane.
EDIT: shane have a look at this: [https://ubuntuforums.org/archive/index.php/t-1565846.html](https://ubuntuforums.org/archive/index.php/t-1565846.html)

---

### Post by shane_faulkinbury2 on 2017-01-06
Hmm, no scanner was found.  I don't understand because I get the root item scanned in my Pictures library.

---

### Post by shane_faulkinbury2 on 2017-01-06
Nor in scsi!

```
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST1000DM003-1CH1 Rev: HP34
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: hp       Model: DVD-RAM SW820    Rev: UH06
  Type:   CD-ROM]
```

---

### Post by Autodave on 2017-01-07
All I can offer you is to uninstall the program and reinstall. (If you haven't tried that yet.)

---

### Post by shane_faulkinbury2 on 2017-01-08
I removed xsane and reinstalled and it still scans as a root document.  So I changed the saves pictures to /home/bubba/Pictures/ and the Type to JPEG and it still saves as out.jpeg root picture.

---

