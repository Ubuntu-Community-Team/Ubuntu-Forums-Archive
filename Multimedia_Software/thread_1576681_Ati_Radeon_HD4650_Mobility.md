---
title: "Ati Radeon HD4650 Mobility"
date: 2010-09-17
forum: Multimedia Software
---

### Post by wh1sky on 2010-09-17
Hello.
I have a problem with installing drivers for ATI Radeon HD4650 Mobility on my notebook HP. 

I downloaded driver from official site of Ati Radeon. After that I use command: ```
sudo sh "packagename.run"
``` 
After that installer (like in windows) opened and I follow the instructions. When it comes to end I go to terminal and use command "aticonfig --initial". That should do something with xorg if I understood right in manual of drivers. 

But after that I restart a computer and system works pretty slow. When I try to move windows it's stucking and so on --> graphic problems. Before installing all was good (default drivers which comes with debian). 

So I'm asking if I need to edit xorg.conf file or anything to make this driver to work? 

I'm using ubuntu 10,04. 

I'm sorry if similiar thread is posted, I used search many times today and I didn't found right thread/solution. 

Thanks for help in advance

---

### Post by Yellow Pasque on 2010-09-17
Remove the driver: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

Install using this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

---

### Post by wh1sky on 2010-09-17
Thanks for help. 
Already I'm working on it. I have just one question. Do I need to work that with stopped gdm?

---

