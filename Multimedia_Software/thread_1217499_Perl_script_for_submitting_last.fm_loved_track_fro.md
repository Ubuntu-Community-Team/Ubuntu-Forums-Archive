---
title: "Perl script for submitting last.fm loved track from Exaile"
date: 2009-07-19
forum: Multimedia Software
---

### Post by rarbox on 2009-07-19
So Exaile's last.fm plugin does not have an option to let you submit your current playing track to Loved Tracks on last.fm. This script will let you do it from the command line.

Download the script from [http://www.rarbox.com/lovefm.tar.gz](http://www.rarbox.com/lovefm.tar.gz) (If the link is down, try again later. I'm hosting it from home on a slow connection)

This script uses the last.fm commandline client which was written by toc-rox on last.fm, and the lovefm.pl script was written by myself.

To get started, extract the files to ~/.lastfmcli/ and follow the instructions below.
-----------------------------------------------------------------------------------------------------------------------------------------------------
Step 1. Run 

```
./lfmCMD.pl method="auth.getToken"
```You will then find your token in a file named last.fm.Response.xml

Step 2. 
Visit http://www.last.fm/api/auth/?api_key=0996e89f272c714ec0bd463ea17faf6c&token=<TOKEN>
Replace <TOKEN> with your token from Step 1) and grant permission to the script to access your account.

Step 3. ```
Run ./lfmCMD.pl method="auth.getSession" token="0000000000000000000000000000000000"
```Replace the token with the one you got from Step 1.
        
Step 4. Check last.fm.Response.xml again and you will find your session key. Edit sk.txt and paste your key there.
-----------------------------------------------------------------------------------------------------------------------------------------------------
Now you're ready to run lovefm.pl. To make things easy, you can add an alias to bashrc

Open ~/.bashrc in any text editor and add the following.

```
alias lovefm="perl /home/whatever/.lastfmcli/lovefm.pl";
```Save it and type:
```
source ~/.bashrc
```-----------------------------------------------------------------------------------------------------------------------------------------------------
**Note:** If you get an error saying a file was not found in @INC, you will need to install those perl modules, which are available in your repositories or from cpan.
-----------------------------------------------------------------------------------------------------------------------------------------------------

You can now type lovefm from the commandline and it will submit the current playing track on Exaile to your Loved Tracks on last.fm

If everything went well, this is what you will see. 

[IMG]http://img40.imageshack.us/img40/9408/lovefm.png[/IMG]

Enjoy.

lfmCMD.pl is capable of using all the last.fm API commands, so if you do some tests with it, please let its author know the result.

---

