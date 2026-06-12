---
title: "Proxy settings in 12.04"
date: 2012-03-21
forum: Networking &amp; Wireless
---

### Post by pmatos on 2012-03-21
Hi,

I have to setup a proxy with authentication and exceptions in 12.04 and I am running into trouble.

If I use the automatic way, through a script I don't know how to setup authentication. Since the script is company wide doesn't contain authentication information.

I can select Manual and insert all the url/ports/authentication information right on the boxes but then there is no place to set exceptions. domains which should use proxy.

Any ideas on how to sort this one using any of the above methods?

Cheers,

Paulo Matos

---

### Post by ChriWo on 2012-04-24
I have exactly the them problem only answers?

---

### Post by pmatos on 2012-04-24
> **ChriWo said:**
> I have exactly the them problem only answers?

Couldn't find solution yet. Sorry. :(

---

### Post by ChriWo on 2012-04-24
OK, many thanks I will continue to search.

---

### Post by r-mo on 2012-04-25
For the ignored hosts issue, try installing dconf-tools using the software centre or
```
sudo apt-get install dconf-tools
```

Then run dconf-editor 
```
dconf-editor
```

Expand System and select proxy, there should be an option for ignore-hosts.  Read the description and add your exceptions comma separated in single quotes.  This should work for all your desktop apps.  

---
The reason I was searching on proxy issues is to do with updates though.  I've set up proxy configuration for apt by creating a file /etc/apt/apt.conf.d/02proxy with the entry
```
Acquire::http::Proxy "http://proxy.example.com:80";
```
As just setting it the GUI way through system settings doesn't appear to work any more.  But, even then, when something like flash gets updated it runs /usr/lib/update-notifier/package-data-downloader without any proxy settings!  The only workaround I've found so far is to open a root terminal
```
sudo -i
```
Set the proxy settings
```
export http_proxy=http://proxy.example.com:8080/
export https_proxy=http://proxy.example.com:8080/
```
and then run package-data-downloader from the root terminal
```
/usr/lib/update-notifier/package-data-downloader
```
Anybody know how I can get root to recognise the proxy automagically?

---

### Post by lildude on 2012-07-22
> **r-mo said:**
> 
Anybody know how I can get root to recognise the proxy automagically?

You can add a script to /etc/profile.d/ that will set the shell level proxy for all users, including root.

---

### Post by lildude on 2012-07-22
You could create an interactive shell script which uses gsettings to set the various proxy settings you require and prompt the user for things like authentication information.

Example usage of gsettings for proxy stuff:

```
gsettings set org.gnome.system.proxy.socks host '127.0.0.1'
gsettings set org.gnome.system.proxy.socks port 3128
gsettings set org.gnome.system.proxy mode 'manual'

# to disable proxy:
# gsettings set org.gnome.system.proxy mode 'none'
```

---

### Post by huu2011 on 2012-09-20
lildude,
Please,kindly share with me how to ```
You can add a script to /etc/profile.d/ that will set the shell level proxy for all users, including root.
```.
I have the same problem for sometimes now.

thank you in advance

---

### Post by lildude on 2012-09-20
> **huu2011 said:**
> lildude,
Please,kindly share with me how to ```
You can add a script to /etc/profile.d/ that will set the shell level proxy for all users, including root.
```.
I have the same problem for sometimes now.

thank you in advance

Sure, just create a file in /etc/profile.d/, for example /etc/profile.d/proxy, and add the following to it:

```
export http_proxy=http://your.proxy:port
export https_proxy=http://your.proxy:port
```

You can also set "ftp_proxy" and "no_proxy" which I hope are self explanatory.

If you use Network Manager to set your proxy via the GUI, clicking the "Apply system wide" button actually populates the /etc/environment file with your proxy info and this should be automatically pulled into your user environments when they login if readenv=1 is set in the /etc/pam.d/* file appropriate for the login method.

HTH

---

### Post by aasullivan1618 on 2013-08-13
lildude,

I hope it's not inappropriate for me to be posting this followup here, I'm kind of a n00b in these forums.

I've been exploring on the web for a while now for how to programmatically change the ubuntu 13.04 (hopefully not erroneously considering it the same as 12.04) system socks proxy in an equivalent manner to using the GUI method.  The GUI is great - I click on "Network Proxy", flip the method switch to manual, then hit "Apply system wide", throw in my password and bam, almost all my stuff is going through that proxy.  But I really can't stop there, I need to go one step further and put those four actions into one even easier shell script.  

Your post brought me to the next step in my search, namely about the /etc/environment population.  Indeed, when I use that GUI to change the proxy, the correct line does show up in /etc/environment.  However, if I change /etc/environment by hand, the same results do not take affect.  Namely Chromium will not switch over to the new proxy settings, even though it does when I use the GUI method.  

I also noticed that the GUI method changed org.gnome.system.proxy mode from 'none' to 'manual' as well as populating the /etc/environment file.  However, even when I change both to look correct in a script, Chromium will still not use the proxy settings.  Is there a third, or maybe 4th 5th or 6th thing that the GUI tool is also doing?

Thanks in advance for the help,

Aaron

---

