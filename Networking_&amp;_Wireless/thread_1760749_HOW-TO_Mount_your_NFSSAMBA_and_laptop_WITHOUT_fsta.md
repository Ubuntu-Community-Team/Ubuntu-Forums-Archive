---
title: "HOW-TO: Mount your NFS/SAMBA and laptop WITHOUT fstab or automount, but with UPSTART"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by deckoff on 2011-05-17
Why this tutorial - I run Kubuntu 10.10 on my laptop. I mounted my NFS drive via /etc/fstab/ as decribed in millions of tutorials. Most of the time the laptop sits in home, but when I am away, accessing the mounted, and not present drive will hang the system. It will result in really slow shutdowns and restarts ( about 10 minutes), too. 
I discovered that the proper linux way is to mount the drive via automount. Unfortunately, this did not work as expected - most of the time once the drive was not present, it will unmount and I had to mount it manually - which  is nothing near auto...
The main reason for doing this is provide is to make my laptop mount to my NFS when I am connected to my home wifi network, and not mount when I am not at home. AND provide fast shutdown or restart(caused by the system not shutting down the wifi network first, and trying to umount after that). AND spare me any hang ups or slow shutdowns. 
In a few words -** automated, easy  and trouble - free way to use your laptop with your NFS.**
The solution is and upstart conf file
Here is the solution 

```
description    "Automounter on default network"
author        "deckoff/deckoff@gmail.com"

start on net-device-up IFACE!=lo
stop on networking stopping
stop on net-device-down IFACE!=lo

env wifiD=deckoff        #SSID(name) ot the wireless network where the NFS is connected
env mIP=192.168.1.106        #local IP of of the NFS
env mDIR=Public            #default mounted dir
env lDIR=MyBookLive        #the local place where the NFS is mounted to. The script mounts in a dir into /media/
env moptions=username=***,password=***,iocharset=utf8,file_mode=0777,dir_mode=0777,soft,noperm        #options for your mount - username, password, iochart etc



post-start script


wifi="'$(/sbin/iwconfig eth1 | egrep ESSID | cut -d '"' -f 2)'"

      if [ $wifi = "'$wifiD'" ]; 
    then 
      mount -t cifs //$mIP/$mDIR /media/$lDIR -o $moptions
      fi
end script


post-stop script

sleep 2
umount /media/$lDIR -f

end script
```

**There are a few variables, you should fill in, before this to work. I made some comments what goes where, and I have given my attributes, but I assume one knows how to manually mount a NFS drive, and cifs is installed.**

Copy and save the file as something.conf( I use NFS.conf). The .conf extension is MANDATORY. Copy the new file to /etc/init . [B]You have to be root to do that!!!! 
[/B]No need to set executable or any special read/write permissions.
The sleep option in the post-script part is vital for me. If not present, the umount will fail for me, so be sure to include it


This setting might be needed, to make this work with resume /hibernation. Check if it works with you first:
> This is  actually restart wireless module after suspend|hibernate. I use  it cause  after some fiddling with the system the module will show it  is  connected, but wont actually work ( no net connection) Restart  solved  the problem, so I fixed it that way: 
My computer with Xubuntu  feisty had a  problem with getting an  ip-adress after waking from  hibernation. I´ve  solved this problem by  changing /etc/default/acpi-support
Editing this file, look for the line below, where to add [networking] after that no problems anymore:

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"


Hope this will work for you to,
Thomas.


1. I would love to hear your opinion on this upstart conf file. I spent a few weeks doing it ( I am a dentist, so I had to learn everything from scratch) how can it be improved, ect.
2. I would be glad if this works for you.
3. What is next - I would love to include an option, witch will ping the NFS any few seconds and check if it there, and umount it if not. This conf file ensures the NFS is mounted until you are connected to the right network. If the NFS fails, the system will hang. Adding a ping check will ensure the system will continue to work, even if the NFS has failed.
Please, share your thoughts :):):)

---

