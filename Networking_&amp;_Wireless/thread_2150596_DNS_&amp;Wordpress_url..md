---
title: "DNS &amp;Wordpress url."
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by jamstir on 2013-06-01
Hi guys and girls, anyone install wordpress? I have a great looking site 3rd finished using this program, then i thought i better add the domain name, "tobots.co.uk" So i set up a front page to tell people that the site is still being built then went into my domain provider and got the dns settings, then went into linode and played with them dns settings. lol I then tested by doing ping and tracer and both are hitting my ip of the server, i then went into W-P and changed site url and W-P url to both say [http://www.tobots.co.uk](http://www.tobots.co.uk)    

Where to my shock i have now lost all power to login as admin, view the site and in general do anything. lol Not to worry i got the website back again by going into wp-config.php/themes/responsive/function.php and adding an update_option for site url and "home" url. Which leads me to my question, if i can ping tobots.co.uk and tracer and i hitting the server why then is my site not being served? I have been everywhere trying to find out the problem, etc/hosts  etc/hostnames/ etc etc, and its got me baffled, can any of you guys share a thought or 4 ? 

I only have an A record, no AAAA or MX set up yet. Does this lead to problems, i getting ready to install Bind9 and take the dns records to it. But i feel its a really small problem to do with site path or something, and one i cant find. lol :(

Anyways, any help would be great ..:KS

---

### Post by ahallubuntu on 2013-06-01
~

---

### Post by jamstir on 2013-06-02
Thanks for helping me on this, yea i have apache2 set up and running, this is my config:

 <virtualhost *80>
    ServerAdmin webmaster@localhost

   DocumantRoot /wordsupply/
  ServerName [www.tobots.co.uk]("http://www.tobots.co.uk")
  ServerAlias [www.tobots.co.uk]("http://www.tobots.co.uk")  tobots.co.uk

   <Directory />
             Options Indexes FollowSymLinks 
             AllowOverride all
  </Directory>
   <Directory>  /wordsupply/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
               Order allow,deny
               allow from all
             </Directory>


Really what i did with apache was copy the default file that echo,s "Hellow World! and then just made a few changes, if i change wordpress url home & site back to the ip address it will show in a browser. I would like to config apache so i can build more sites and just point it to the directory, which i feel i have done with apache. Or maybe not, what you think? One thing i have done is remove the /var/www file cause the website is set up away from the home folder and into a system file. The folder or Directory as linux people like it to be called, is a www-data file with wordpress being able to write to it, i can't see this being a problem. I have looked at a lot of ways to set apache2 up and i feel i not got the right way here to be able to build many sites on the one ip address, this being called the "Name-based Virtual Host" way. Can anyone please help guide me through the process, i have apache 2.2.22 installed with no other work done bar coping the default file, i will however point this fact out again, just in case this is a problem, i DON'T have my wordpress site installed in the /var/www/wordpress, i have it installed away from home folder in a directory called /wordsupply/ i thought i would name it this cause this is my supply website and next to be built will be the CtoC site. Not sure if this is a problem for Apache. 

Thanks again for you reply and anyone else that can help me with this.

---

### Post by jamstir on 2013-06-03
Anyone? LOL.  While here to, i noticed that Ubuntu are now asking to donate a few bucks for the latest ubuntu 13.04.
Is ubuntu going to be heading away from free OS to paid? I had a thought of putting there OS on a tablet about a year ago, seem ubuntu beat me to it, although i do feel now that smart phones tablets and such like are now being played out, even facebook got a smart phone. And i hear a lot of complaints now a days about apps in the google store being hard to promote, not shocked to hear that at all if you allow one company to control over 70 to 80% of where the apps can be found. Anyways, will head into Apache here and see if i can get this set up before hitting the Chinese brandy in the afternoon.

---

### Post by ahallubuntu on 2013-06-03
~

---

### Post by jamstir on 2013-06-04
Haaa no worry bro, i think i got apache set up right, i now have:

Listen 80

NameVirtualHost *:80

<VirtualHost *:80>
       ServerAdmin [email]webmaster@www.tobots.co.uk[/email]
       DocumentRoot /wordsupply/
       ServerName tobots
       ServerAlias [www.tobots.co.uk](www.tobots.co.uk)

</VirtualHost>

The NameVirtualHost was throwing a warning up saying something about having no Virtualhosts, and the socket being used twice, so therefore it failed to start, after some fine Brandy and 2 hours reading, lol i found that in the /etc/ports.conf i needed to remove this line NameVirtualHost *:80 .. And then all started fine with no error given.

I still not pulling the the website using the FQDN, so i did a little work on the DNS zones again and have to wait a few hours now to see if it starts working.

I found this all confusing cause of the amount of settings for apache and hosts etc having to match each other and different browsers treat things in other ways, and i still not 100% clear on apache, i think it will be looking for HTTP header in the website when asked from a domain name, like i say all confusing, but plenty of help in the forums, thanks for pointing me to apache bro.

---

