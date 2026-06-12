---
title: "Create mount from a web page"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by berty1 on 2011-03-15
Hi,
 
I hoping someone can help me with this problem.
 
I am trying to use a web page button to mount my NAS box and am getting the following error when I try to mount:-
 
mount error: permission denied or not superuser and mount.cifs not installed SUID 
 
 
Here is my entry in the fstab:- 
 
//hs-dhgl000/ubuntu /mnt/buffalo smbfs users,noauto,password= 0 0
 
 
 
Here is the php code in my web page:-
 
 
//if clicked the mount button lets try and mount it
if ($mountNAS==1) {
//mount the NAS drive
//this trys to mount all that is in the fstab file
//$command="mount -a";
//$command="smbmount //hs-dhgl000/ubuntu /mnt/buffalo rw";
 
$command="mount /mnt/buffalo";
 
system($command,$return);
if ($return=="0") {
echo("The NAS Mount is successfull <br>");
} else {
echo("The mount has failed." . " return = " . $return . "<br>");
//quit the script as the mount failed
exit();
}
}
 
I can mount from the ubuntu box OK using the mount command.
 
I have read somewhere that only the 'owner' of the mount can mount.
 
Any help appreciated...

---

