---
title: "Sudden sound issue - Need help!"
date: 2014-05-22
forum: Multimedia Software
---

### Post by arnold_layne2 on 2014-05-22
I was forced to hard boot my laptop while running Ubuntu 13.04, and after that the OS seems to have lost it's sound capability.
I've been following the Troubleshooting guide here:[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

I've reached Step 3 without any luck.  
Here's partial output to [COLOR=#333333][FONT=UbuntuMono]./alsa-info.sh

[/FONT][/COLOR]

```
!!ALSA Version
!!------------


Driver version:     k3.11.0-12-generic
Library version:    
Utilities version:  1.0.27.1

```

As you can see my library version is completely blank. Any idea what might've gone wrong here? The guide says nothing about what to do if the Library version is blank. 

[http://pastebin.com/DdF62JZ9](http://pastebin.com/DdF62JZ9) 
This is the entire output to ./alsa-info.sh

---

### Post by Yellow Pasque on 2014-05-22
See if this help with the lib problem:
```
sudo apt-get install --reinstall libasound2
```

---

