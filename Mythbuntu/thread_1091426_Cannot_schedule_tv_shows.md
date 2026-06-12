---
title: "Cannot schedule tv shows"
date: 2009-03-09
forum: Mythbuntu
---

### Post by 4ebees on 2009-03-09
Okay, this is one of those 'gun to head' moments.

I **had** a nice system running:

Mythbuntu 8.04.1
P4 3Ghz
1.4G RAM
160G and 500G HDD
Two PVR-150 PCI Hauppauge tuners (though I think I've been sold a dud on one of them)
nVidia 128Mb RAM MX4000

All was well. I then decided to add our family photos to the Myth box. Inadvertently I added them all to /sda1/ and maxed out the space available.

This caused me to receive a 'cannot connect to database message' from which I couldn't recover (even after moving the photos).

I've got an Ubuntu desktop running on the machine too. So I uninstalled Myth and reinstalled.

Everything in general is fine now EXCEPT I cannot schedule tv shows.

The 500G HDD is mounted under /video and I use this for storing tv and video.

I can watch TV and when I run:

cat /dev/video0 > file.mpg

I can record tv to the /video partition, but each time I try to manually schedule a show (which I'd done lots of times prior to my current screw up) it does not save the setting and tells me I haven't scheduled anything.

This is driving me crazy as I cannot work out what the problem is.

I know I should have left well enough alone and NOT screwed the system.

I'd appreciate any assistance offered at this stage :)

For what it's worth, I've installed the Shepherd EPG and it claims to be running fine, but it does not show up in the programming guide section of myth (????).

Again, any assistance or referrals would be most appreciated.

---

### Post by 4dognight on 2009-03-09
> **4ebees said:**
> 

For what it's worth, I've installed the Shepherd EPG and it claims to be running fine, but it does not show up in the programming guide section of myth (????).



I would have to think your program guide isn't being inserted properly. If there is no guide data, it cant schedule anything. Look for errors there. It could be permissions on the database.

---

### Post by 4ebees on 2009-03-09
> **4dognight said:**
> I would have to think your program guide isn't being inserted properly. If there is no guide data, it cant schedule anything. Look for errors there. It could be permissions on the database.

Hi 4dognight.

Thanks for the information.

I'm afraid I'm not certain HOW to check permissions on the database. Any clues? :))

Also, should it not allow me to manually schedule shows (which is what I'm trying to do)?

Regards,
4ebees

---

### Post by 4dognight on 2009-03-09
you could try installing mysql browser or mysql administrator. You can use them to connect to the db/and or change the permisiions via a gui.

Do you have guide data when you open the EPG? I was under the asumption you have no guide data. Have you checked your backend log for unusual messages?

---

### Post by 4ebees on 2009-03-10
Hi 4dognight,

> **4dognight said:**
> you could try installing mysql browser or mysql administrator. You can use them to connect to the db/and or change the permisiions via a gui.

I'll install the GUIs and see how I go.


> **4dognight said:**
> Do you have guide data when you open the EPG? I was under the asumption you have no guide data

That's right. Though Shepherd says everything is alright and up and running, it does not populate the program section of the Myth GUI.

> **4dognight said:**
> Have you checked your backend log for unusual messages?

Where is it that I can find the logs for this?

Again, many thanks.

---

### Post by 4dognight on 2009-03-10
logs are at

backend log is /var/log/mythtv/mythbackend.log
frontend log is /var/log/mythtv/mythfrontend.log

you can also test your database connection via command line.

mysql -h <*host> --user mythtv --password mythconverg
enter your password
enter exit; to get out of the command line tool for mysql




*host is how you set up your backend IP in the config

could be 127.0.0.1 or actual IP if you entered one

---

### Post by 4ebees on 2009-03-11
> **4dognight said:**
> logs are at

backend log is /var/log/mythtv/mythbackend.log
frontend log is /var/log/mythtv/mythfrontend.log

you can also test your database connection via command line.

mysql -h <*host> --user mythtv --password mythconverg
enter your password
enter exit; to get out of the command line tool for mysql




*host is how you set up your backend IP in the config

could be 127.0.0.1 or actual IP if you entered one


Hi 4dognight.

Attached are the front and back end logs. They both contain a number of errors which I don't understand (unsurprisingly).


Many thanks for you help with this.

Regards,

4ebees

---

### Post by 4dognight on 2009-03-11
I assume you have a master backend and a slave backend, by looking in the logs.

Looks like you use the loopback address and static IP. You should try to be consistent and use static IP. 

Most notibly I saw this message.

2009-03-11 00:27:47.281 This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database.

Are your slave and master backends running different versions? This could be why your not populating guide data.

---

### Post by 4ebees on 2009-03-12
> **4dognight said:**
> I assume you have a master backend and a slave backend, by looking in the logs.

Looks like you use the loopback address and static IP. You should try to be consistent and use static IP. 

Most notably I saw this message.

2009-03-11 00:27:47.281 This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database.

Are your slave and master backends running different versions? This could be why your not populating guide data.


Hi again,

The front/back end are on the same machine. 

So OH! DOH! and SO FAR SO CLOSE!

:)

OH! = I updated everything I could get my hands on :)

DOH! = I then changed the IP addresses so they were both 127.0.0.1 and now I can manually schedule a recording

SO FAR SO CLOSE! = there is still no TV program listing showing.

That said, manually setting the recording is fine and if I can't progress past that, I'm not particularly worried at all.

Thanks ever so much for your patience and assistance. It is very much appreciated. 

If you can help me get these things showing, that will be great, but at present I can honestly say that I'm very happy (and somewhat embarrassed for not having thought that through myself :oops: )


:popcorn:

---

