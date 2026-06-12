---
title: "How to fix &quot;Desktop Effects aren't enable&quot; for intel integrated graphic in Jaunty"
date: 2009-05-10
forum: Multimedia Software
---

### Post by wantakill on 2009-05-10
First, I just a newbie in Ubuntu, so if there is any mistake, please let it go. After searching few posts about the compiz problem on Ubuntu 9.04.

I combine some and find a good solution 

First, download Forlong's compiz-check

You can use this command to download it to your home directory:
```
wget http://blogage.de/files/9124/download -O compiz-check
```

Afterwards, you have to make it executable:

```
chmod +x compiz-check
```


And finally run it like this:

```
./compiz-check
```

If they output shows that Your intel graphic card is in the blacklist, this is the perfect solution for you.

 Edit the compiz script file
```
sudo gedit /usr/bin/compiz
```

Then go down and look for blacklist, then add the # to take your intel graphic out of the blacklist.
Then the script should look like this

```
# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2a02 " # Intel GM965
#T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T
```

Save, then restart

After reboot, go to System > Preferences > Appearance >Visual Effects 
then tick on the middle or the last option.

Now your compiz should work back as normal.

My computer work perfectly for this, Hope this will help

---

### Post by kennyschiff on 2009-05-28
worked for me

---

