---
title: "Mythtv mythbackend not starting on boot"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by cauly on 2006-10-17
I followed the instructions below to get mythbackend to kick in on boot. I commented out the bit in the mythtv-backend script that modprobes for pcHDTV as I don't use it and don't have the module anyhow.

# wget [http://patrick.wagstrom.net/tutorials/mythTV64/files/mythtv-backend](http://patrick.wagstrom.net/tutorials/mythTV64/files/mythtv-backend)
# sudo chmod +x mythtv-backend
# sudo mv mythtv-backend /etc/init.d/mythtv-backend
# sudo update-rc.d mythtv-backend defaults
# sudo /etc/init.d/mythtv-backend start

This starts fine with NO errors when in X using the 'sudo /etc/init.d/mythtv-backend start' command.

On reboot it does not show mythbackend running at all, looked through a few logfiles but no joy nothing showing me why it didn't start. :confused: 

Running Ubuntu Dapper 6.06LTS ( 2.6.15-27-386 kernel) with Mythtv 0.20 compiled from source with all the plugins running sweet :) just need this sorted and I am cooking on gas as they say (bar a slight problem with IR device on my DVB-T card as it is not supported yet)
Running an Athlon 64 3200+ but I am guessing it should not matter that I have ubuntu running 386 (naughty I know!), this shouldn't affect it, should it? ;) 

Any help would be much appreciated!
 
Cauly

---

### Post by teet on 2006-10-17
> **cauly said:**
> I followed the instructions below to get mythbackend to kick in on boot. I commented out the bit in the mythtv-backend script that modprobes for pcHDTV as I don't use it and don't have the module anyhow.

# wget [http://patrick.wagstrom.net/tutorials/mythTV64/files/mythtv-backend](http://patrick.wagstrom.net/tutorials/mythTV64/files/mythtv-backend)
# sudo chmod +x mythtv-backend
# sudo mv mythtv-backend /etc/init.d/mythtv-backend
# sudo update-rc.d mythtv-backend defaults
# sudo /etc/init.d/mythtv-backend start

This starts fine with NO errors when in X using the 'sudo /etc/init.d/mythtv-backend start' command.

On reboot it does not show mythbackend running at all, looked through a few logfiles but no joy nothing showing me why it didn't start. :confused: 

Running Ubuntu Dapper 6.06LTS ( 2.6.15-27-386 kernel) with Mythtv 0.20 compiled from source with all the plugins running sweet :) just need this sorted and I am cooking on gas as they say (bar a slight problem with IR device on my DVB-T card as it is not supported yet)
Running an Athlon 64 3200+ but I am guessing it should not matter that I have ubuntu running 386 (naughty I know!), this shouldn't affect it, should it? ;) 

Any help would be much appreciated!
 
Cauly

I'm running edgy with mythtv 0.20 from the repos...

I had this same problem.  I fixed it by going to system --> administration --> users and groups.  Then I chose my account (alex) and then clicked on the properties button.  In that dialog box, I chose the advanced tab up top and then changed the "Main Group" of my account from 'alex' to 'mythtv'.  

Note:  'mythtv' was the user created during the install process.

-teet

---

### Post by cauly on 2006-10-18
OK Thanks teet for that.

I think I have managed a work around (not ideal) but it works so far, I have added mythbackend to the Sessions startup (like you normally do for mythfrontend?)
It's working as it does not need to switch to root/sudo for anything as it is doing everything via mysql DB which it has access to anyway.
I guess I will run into some problems later but I have tested everything I can think off and it looks good.
It seems to be running quicker under my own username.

Now to sortout my channel lineup which is all over the place! :rolleyes: 

Cheers!

Cauly

---

