---
title: "Automount AD share + Centrify"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by aspen093 on 2011-02-09
Hi All,

I have a bunch of old laptops at the school I work at and Windows has been doing them no favors. I am experimenting with putting xubuntu on them to pep them up a bit. We do, however, use Active Directory for authentication which is requiring a bit of finagling to set up under linux.

I am now able, thanks to centrify express (the repo version) to log in to AD accounts. My next step is to set up auto mounting of user directories, which is proving a bit of a head ache. 

I have been looking around a lot and have found various ways of doing this in instances where the path to the share is simply:
//server/user 

But in my case, we have the shares set up to go to
(if a student) //server/students/<year>/<username> 
#students is a AD group by the way, of which <year> is a sub group and <username> is a member of.
(if not a student) //server/<group>/<username>

Now, if I was logging into a windows client, AD would pass these paths directly to the client, but in linux this does not seem to happen easily.

How do I go about setting up these shares to automount at login for each user? Is there a way I can pull that path from AD? Or do I have to build it on the client?

Thank You!
Nick

---

### Post by unixisfun on 2011-02-11
hi Nick
Its great idea to re-use laptops for installing xubuntu as they require very less processing power. Based on my past experience with the Centrify product (btw, its an excellent product), with Auto Zone, UNIX attributes, such as UID, default shell, and home directory, that are normally defined in the zone to which the UNIX computer is joined, are derived from user attributes in Active Directory, or from configuration parameters in /etc/centrifydc/centrifydc.conf. By default or out of the box, the product will create home directories located on the Ubuntu server or desktop. So you have to tell it to use the AD attributes (if its pointed to the server hosting the home dir).  I know that their paid version has all these hooks, but need to check their express offering. Why don't you post this question on their Express forums and see. Its free to register. I had most of my questions answered through their forums.

[http://community.centrify.com/t5/DirectControl-Express/bd-p/DirectControl](http://community.centrify.com/t5/DirectControl-Express/bd-p/DirectControl)

---

### Post by aspen093 on 2011-02-27
Thank you for your reply unixisfun! I'll go ahead and do that then. It hadn't even really occurred to me that centrify could use the AD attributes. (I was trying to find a way to get those from centrify and wasn't very successful.) I hope someone on the centrify forums will have an idea! :)

Thank you again!
Nick

---

### Post by sumana on 2011-03-14
For completeness sake, I am posting the solution proposed by Centrify support to Nick here.

You could also follow the post on Centrify express forums : [http://bit.ly/dM7mmZ](http://bit.ly/dM7mmZ)

Thanks
Sumana
Centrify Support

-------------------------------------

Maybe you can try the following script to mount the home directory path specified in AD:
 
 
============
#!/bin/sh /usr/share/centrifydc/perl/run
 
# This script uses ldap to fetch user homeDirectory from AD and mount/umount by smbmount and smbumount
 
use strict;
#use MIME::Base64;
use File::Spec;
 

# get base dn
 
my $zone_base = `cat /var/centrifydc/kset.zonename`;

#get user CN

my $cn = `adquery user -D ${ARGV[0]} | cut -d, -f1`;
#print $cn;

my @cn = split(/\n/,$cn);

#ldap search
#search for the homeDirectory attribute of user in AD in autozone mode
#also cut the path out and change backward slash to forward slash
my  $ldap = `/usr/share/centrifydc/bin/ldapsearch -Q -H "LDAP://" -b  "$zone_base"  -LLL "(@cn)" homeDirectory | grep homeDirectory | cut -d:  -f2 | sed 's:\\\\:/:g' `;

#print $ldap;
#split the output into single line
my @line = split(/\n/, $ldap);
#print @line;
#if ldapsearch result is not blank
if (@line )

{

    if(${ARGV[2]} eq "mount") {

#mount the homeDirectory with smbmount command on mountpoint with kerberos ticket

    my $mount = `smbmount @line ${ARGV[1]} -o sec=krb5i`;
#    print "mount";
    }
}

#if argument3 is umount will umount the share
    if(${ARGV[2]} eq "umount" ){

    my $mount = `smbumount ${ARGV[1]}`;
#    print "umount"
    
    }    


 
=========
 
Usage:
 
adhome.pl <username> <mount point> <mount/umonut>
 
e.g.
mount homedirectory on /home/username/share:
 
adhome.pl testuser ~/share mount
 
unmonut  /home/username/share:
 
adhome.pl testuser ~/share umount
 
 
 
Then perform the following step:
 
1.       Place the script  into a specific location e.g. /tmp/adhome.pl
 
2.       chmod +s `which smbmount`
 
3.       chmod +s `which smbumount`
 
4.       create a folder in /etc/skel so every user will have this folder(mount point) when new home directory is created
 
e.g. /etc/skel/share
 
5.       edit /etc/profile to invoke the script whenever user login by adding
 
/tmp/adhome.pl $USER ~/share mount
 
6.       edit /etc/skel/.bash_logout to invoke script (Terminal login) for unmounting the drive by adding
 
/tmp/adhome.pl $USER ~/share umount
 
7.       edit /etc/gdm/PostSession/Default to invoke script (GUI login) for unmounting the drive by adding
 
/tmp/adhome.pl $USER ~/share umount
 
Thanks,
Ian
------------------------------------------------

---

