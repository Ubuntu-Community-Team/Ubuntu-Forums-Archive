---
title: "Help installing Torrentflux-b4rt"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by PogMoThoin on 2009-01-02
Hi

I've been trying to install torrentflux b4rt on my server using [this guide]("http://ubuntuforums.org/showthread.php?t=848138") but always get a problem as there is no phpmyadmin page in /var/www/. When installing "apt-get install php5-cli php5-gd phpmyadmin zip unzip unrar libxml-dom-perl libxml-simple-perl libthreads-shared-perl libhtml-parser-perl transmission-cli libdigest-sha1-perl" I did get some sort of choice for phpmyadmin, whether to use apache2, apache...... and I picked the first one, apache2

I've tried several times to do it manually by creating the user "torrentflux" in MySQL using Webmin by doing the following:
> On the MySQL main page, click "User Permissions", and then "Create new user". Enter the following, and make sure to select the appropriate radio buttons:

    * Username = torrentflux,
    * Password = *enter a password which you will add to the config.php file later*,
    * Hosts = localhost,

Don't select any of the permissions, and Save.
and gave the following permissions for a database called "torrentflux"
> * Select table data,
    * Insert table data,
    * Update table data,
    * Delete table data,
    * Create tables,
    * Drop tables,
    * Alter tables.

Can anyone help here? I've just done a clean install again, I've torrentflux-b4rt uploaded to var/www/ and extracted and moved to the folder /var/www/torrentflux. I've not gone any further yet, or created any user hoping someone here will help. I've got no phpmyadmin in the /var/www/ folder, does anyone else know where it is? or is it deleted as phpmyadmin seemed to set itself up.

Thanks in advance,

Pog

Edit: I do have a directory /var/lib/phpmyadmin but this only contains 2 files called "blowfish_secret.in" and "config.inc.php" which is blank

Edit 2: I have a file in /etc/apache2/conf.d but I can't access this from a browser as its not in /var/www

---

### Post by PogMoThoin on 2009-01-02
**Ok, I tried this again and the same thing, I get this when I try to login**

[IMG]http://i419.photobucket.com/albums/pp279/PogMoTho1n/Torrentflux.jpg[/IMG]

**Here's the contents of my inc/config/config.db.php**

> /******************************************************************************/
// YOUR DATABASE CONNECTION INFORMATION
/******************************************************************************/
$cfg["db_type"] = "mysql"; // Database-Type : mysql/sqlite/postgres
$cfg["db_host"] = "localhost"; // Database host computer name or IP
$cfg["db_name"] = "torrentfluxb4rt"; // Name of the Database
$cfg["db_user"] = "torrentfluxb4rt"; // Username for Database
$cfg["db_pass"] = "my password"; // Password for Database
$cfg["db_pcon"] = false; // Persistent Connection enabled : true/false
/******************************************************************************/

?>

**Heres the torrenfluxb4rt user permissions**

[IMG]http://i419.photobucket.com/albums/pp279/PogMoTho1n/torrentfluxuserpermissions.jpg[/IMG]

**Here's the torrenfluxb4rt database permissions**

[IMG]http://i419.photobucket.com/albums/pp279/PogMoTho1n/torrentfluxdatabasepermissions.jpg[/IMG]

**I've manually executed the sql from the file torrentflux/sql/mysql/mysql_torrentflux-b4rt-1.0.sql and created the tables, heres the screenie**
[IMG]http://i419.photobucket.com/albums/pp279/PogMoTho1n/torrentfluxdatabasetables.jpg[/IMG]

**I've set the virtual server in apache to port 80 and set the document root at /var/www/torrentflux/html**

[IMG]http://i419.photobucket.com/albums/pp279/PogMoTho1n/apache.jpg[/IMG]

I'm lost, I've got no idea whats stopping me accessing the database, the database seems to be setup alright, but I just can't access it. Anyone got any idea's before I tear my hair out.

---

### Post by PogMoThoin on 2009-01-02
Anyone, I'm really stuck here

---

### Post by PogMoThoin on 2009-01-03
Ok, I solved it in the end, it was that mysql didn't like my password as it has @ and $ in it, once i choose a simple password it was fine

---

