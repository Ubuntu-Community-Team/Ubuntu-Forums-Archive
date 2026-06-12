---
title: "Can I run Mythbuntu From a raid drive?"
date: 2012-10-03
forum: Mythbuntu
---

### Post by RTIInstaller on 2012-10-03
I have an existing 4.5 TB raid drive installed and running with movies on it, Can I install mythbuntu on the same Raid and simply tell it to save the pre existing content? so that I can use that content as my video storage?

---

### Post by RTIInstaller on 2012-10-04
> **RTIInstaller said:**
> I have an existing 4.5 TB raid drive installed and running with movies on it, Can I install mythbuntu on the same Raid and simply tell it to save the pre existing content? so that I can use that content as my video storage?

I guess the answer is NO!

---

### Post by nickrout on 2012-10-05
> **RTIInstaller said:**
> I guess the answer is NO!Your best bet would be to install a small drive to house the OS (an SSD would be ideal, if you budget works with that) - no more than, say 40G is required. In fact a frontend can be installed in about 10% of that but *buntu can be quite greedy and 4G drives are not exactly plentiful!

Then mount your raid drive which has the data on it and point mythbuntu at it as a videos storage group. You will need to make sure ownership and permissions.

I assume from your other posts (you refer to "clients') that you are a computer professional and know how ownership and permissions work in  *nix.

---

### Post by RTIInstaller on 2012-10-05
> **nickrout said:**
> Your best bet would be to install a small drive to house the OS (an SSD would be ideal, if you budget works with that) - no more than, say 40G is required. In fact a frontend can be installed in about 10% of that but *buntu can be quite greedy and 4G drives are not exactly plentiful!

Then mount your raid drive which has the data on it and point mythbuntu at it as a videos storage group. You will need to make sure ownership and permissions.

I assume from your other posts (you refer to "clients') that you are a computer professional and know how ownership and permissions work in  *nix.

I am an A/V networking install professional. Started installing audio systems about 34 years ago.  I am just now learning Linux,  So yes I am a newbie at this game and no I do not know how to set permissions yet, but I do know how to navigate around a terminal.

I have a 1.5 TB Drive as the main drive and a 4.5 TB Raid 5 that is working but was originally setup with an old Myth TV system 5 years ago which died and is now being replaced with mythbuntu. This system has 5 front end client machines (there used to be 7 but two died and I have not fixed them yet) I have A mythbuntu front end set up on one of them when I get that one to work I will take out the hard drive and clone it to the other drives and then just change the static IP for each.

---

### Post by nickrout on 2012-10-05
Ahh OK I understand your reference to clients better now. I can also see why you seem more impatient than the average poster, clients=pressure (as a lawyer I know the feeling, it's the same client=pressure bizzo!)

In mythtv-setup you can set up storage groups. I guess your raid system is mounted somewhere, I'll call it /raid/path for demonstartion purposes, and that the videos are all under /raid/path/vids. Substitute your own value.

You need the mythtv user to have access to that directory. test it with ```
sudo su - mythtv
ls /raid/path/vids/
touch /raid/path/vids/testfile
```

If both commands come back without error  then you are ready for the next step.

Go back to your usual user (ctrl-d) and run mythtv-setup. Go down to storage groups and add /raid/path/vids/ (note the trailing /) to the Videos storage group. If there is not an existing Videos storage group, create one.

Now exit out of there, go into mythfrontend and go to the videos section. Press th menu button (m on keyboard) and scan for videos.

That's all there is to it really.

---

