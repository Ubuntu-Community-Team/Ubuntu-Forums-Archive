---
title: "BBC iPlayer Parental Control Issue"
date: 2011-01-29
forum: Multimedia Software
---

### Post by JohnMead on 2011-01-29
While trying to get the iPlayer working (Ubuntu 10.10) I turned on parental control and set up all the passwords and other stuff it needed. Now when I try to play something with guidance it says wrong password and also wrong answer to security question. I know 100% I am putting the correct one in so I think I need some help.

---

### Post by shantiq on 2011-01-29
ok john not sure what happened there but i would suggest try again


**First remove**

**Go to terminal**  Applications/accessories/terminal  and enter the following

1. 

```
apt-cache search iplayer

```
2. if you scroll down you will find the name of YOUR iplayer each one has an ID number 

Code:
```
bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1

```


3. then run the usual


Code:
```
sudo apt-get remove bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1
```




**then reinstall  :KS**     and on a lighter note  maybe do not go for the passwords this time:KS

---

### Post by JohnMead on 2011-01-29
Thanks for your reply. 

I had previously uninstalled and reinstalled but tried again using your method. It did uninstall correctly however when I reinstall it is the same.

It does however also remember the programs I previously downloaded so it must be saving its settings somewhere and uninstall is not removing these.

Regards
John

---

### Post by shantiq on 2011-01-29
sorry John really thought it might work iplayer is so convoluted it probably leaves traces in computers one has not yet bought:KS:KS

ok go to Places/computer/File system try and run iplayer in the search see where the files are

**then remove them all**    that should take care of all extra info   ....i hope


although it might be that the problems resides with your passwords on the site

===============================================
**But** as an alternative may i suggest using get-iplayer instead that way you can keep the files longer and protect yourself from the vagaries of internet connection; which is why i started using this instead
**also** then it plays like a normal video no choppy stop and start gremlins


```
sudo apt-get install get-iplayer

```

once installed   run   ```
get-iplayer
```or ```
get_iplayer
```

it will give you a list of all current programs



Then run  

```

get_iplayer --get 607(number of your program)  --nopurge  -v  --subtitles  --vmode=flashvhigh2
```


you can pick  other modes   flashhd   for HD
                            flashhigh

add   --test    to the line above to see what is available for a given program



You can also use the pid address from the BBc site from the url box this way

```
get_iplayer --pid=enter the address   --vmode=flashvhigh2 --nopurge --subtitles
```


that way you have more control over your files
and if you want to you can delete them after viewing



hope this helps

---

### Post by JohnMead on 2011-01-29
Ok - thank you very much for your help

---

