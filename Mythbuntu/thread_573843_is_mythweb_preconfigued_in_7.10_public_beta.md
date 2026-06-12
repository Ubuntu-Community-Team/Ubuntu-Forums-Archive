---
title: "is mythweb preconfigued in 7.10 public beta?"
date: 2007-10-12
forum: Mythbuntu
---

### Post by stevetv on 2007-10-12
hi.  sorry i dont seem to be able to access mythweb from my network.

in mythbuntu control centre, mythweb is checked as a plugin, and ive set a password.

however when i go to [http://192.168.1.4/mythweb](http://192.168.1.4/mythweb) and enter my password, I get only a gray screen with the following

```

Database Access Denied

You are most likely receiving this message because you
have failed to configure mythweb's database login info.

Please see .htaccess for instructions.

```

sorry. do i need to configure mythweb?  

thanks.

---

### Post by superm1 on 2007-10-12
> **stevetv said:**
> hi.  sorry i dont seem to be able to access mythweb from my network.

in mythbuntu control centre, mythweb is checked as a plugin, and ive set a password.

however when i go to [http://192.168.1.4/mythweb](http://192.168.1.4/mythweb) and enter my password, I get only a gray screen with the following

```

Database Access Denied

You are most likely receiving this message because you
have failed to configure mythweb's database login info.

Please see .htaccess for instructions.

```sorry. do i need to configure mythweb?  

thanks.
Steve,

Did you go through and setup mythweb during the install (From live disk) and then change it from the control centre? 

Did you initially set it in the control centre?

---

### Post by stevetv on 2007-10-12
thanks for reply.  yes i did both.

during initial setup, I believe i was asked if i want to use mythweb?  (sorry you will know the specifics... ive only installed mythbuntu twice)..and i wouldve selected yes. and added a password if prompted.  i dont recall been asked anything about a database.. 

the control centre shows plugin section shows that mythweb is selected.  i have changed the password once form control center but that is it.

apparently no one else is having any problem with mythweb.. possible i should just reconfigure it? (err.. im not sure how to do that).

---

### Post by superm1 on 2007-10-12
Well i'm wondering if there is a bug in one or the other.  

If its not working in the control centre, you should be able to reset the password like this too:

```
sudo dpkg-reconfigure mythweb
```

---

### Post by stevetv on 2007-10-12
yes thanks.  that worked perfectly.

i was been prompted for a password previously, and im certain i entered the correct one.  but it just gave me the error i mentioned above.

after i reconfigured with the code you just supplied, it worked perfectly.

thanks.

---

