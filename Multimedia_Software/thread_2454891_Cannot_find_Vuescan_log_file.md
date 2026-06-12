---
title: "Cannot find Vuescan log file"
date: 2020-12-08
forum: Multimedia Software
---

### Post by carusoswi on 2020-12-08
Running Ubuntu 20.04, downloaded the latest VueScan.deb.  Instructions said to click on file and 'software installer' would appear, click on the Vuescan icon, and installation would occur.  That did not work, so I used 'Files' to navigate to the folder containing the .deb file, right clicked, selected GDebi Package installer, and the application installed perfectly.

Now, I have a support question for Vuescan, and, in order to submit a question, I need to attach the log file located in the ~/.vuescan folder. 

I would expect to find this folder under Home, but have had no success.  Can someone explain the proper method to go about finding this folder.  The name of the file is VueScan.log, but until I find the containing folder, I doubt that I shall find it. I know the folder is hidden, but am searching with 'show hidden files' checked.

VueScan support has been helpful to me in the past, but it has been a while, and I do not remember needing to attach the log file in order to post a request for support. Attaching that file is required before the online interface will allow ones question or support request to be sent.

FWIW, I am registered with VueScan's 'Professional' version of the software, and use it to good effect with my Epson V800 scanner.

Any assistance would be greatly  appreciated.

Thanks.

Caruso

---

### Post by CelticWarrior on 2020-12-08
Yes, any folder name preceded by a dot is a hidden folder. Use CTRL+H to show hidden folders/files in your file manager.

---

### Post by SeijiSensei on 2020-12-08
Use the "locate" command. First run "updatedb" to make sure the index is up to date.
```

sudo updatedb
locate VueScan

```

---

