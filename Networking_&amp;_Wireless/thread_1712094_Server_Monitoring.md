---
title: "Server Monitoring"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by ratman99uk on 2011-03-22
Hi All

Does anyone know of a package I can install that can be set to ping my servers/switches every 5min and send me an email if there's no reply. A web based interface would be good so we can see at glance there all online.
I looked at the Ubuntu server guide but the two programs listed are over kill and require software installing on the servers. I also want to monitor the switches and WAPs so I can install software on them.
I tried googleing it and I can find many for android phones and iphones that do it.

Any ideas?

---

### Post by conneco on 2011-03-22
sound like you need a script that runs via cron, should be easy enough to do.

You'll need sendmail installing on the ubuntu box,

this will get you halfway

[http://www.askdavetaylor.com/how_can_my_shell_script_test_server_status.html]("http://www.askdavetaylor.com/how_can_my_shell_script_test_server_status.html")

and this will get you the rest

[http://beingkejo.wordpress.com/2008/05/28/sendmail-in-a-shell-script/]("http://beingkejo.wordpress.com/2008/05/28/sendmail-in-a-shell-script/")

let us know if you need help putting it together

---

### Post by ratman99uk on 2011-03-22
that's great, I will have a go now and get back to you.

Thanks
Paul

---

### Post by pl@yer on 2011-03-22
Since I'm still learning perl, I thought this might be a good little project. 
I know I could have used net::ping module. 
```

~$ cat pingtest.perl
#!/usr/bin/perl
#test ping results 
sub getpingresult () {
foreach my $curline (@pingresult){
chomp($curline);
if ($curline=~/loss/){
$pingres=$curline;
break;
};
};
};

$inputfile="/var/www/test2/index.html";
open FHIN,"<$inputfile" or die $!;
@linearray=<FHIN>;
close FHIN;
open FHOUT,">$inputfile" or die $!;
foreach $line (@linearray){
@curip=split(/,/,$line);
$curip=$curip[0];
@pingresult=`/bin/ping -w 1 $curip`;
& getpingresult;
if ($pingres=~/100%/){
$line=~s/up/down/;
print FHOUT "$line";
`/usr/bin/mail -s "$curip is down" you@somewhere.com</dev/null`;
}
else {
$line=~s/down/up/;
print FHOUT "$line";
}
}


```
web page
```

~$ cat /var/www/test2/index.html
192.168.2.237,up<br>
192.168.2.222,up<br>
192.168.2.99,down<br>

```

---

### Post by ratman99uk on 2011-03-22
Hi Guys

Conneco

i had to change the script that does the pinging becuase the -o switch wasnt supported, i changed it to ping -w 1 which seemed to fix it.
however when i try to send the email using the code in the second page i get:
./pingscript: line 34: $tmp: ambiguous redirect
./pingscript: line 35: $tmp: ambiguous redirect
./pingscript: line 36: $tmp: ambiguous redirect
./pingscript: line 37: $tmp: ambiguous redirect
./pingscript: line 38: $tmp: ambiguous redirect
./pingscript: line 39: $tmp: ambiguous redirect
./pingscript: line 40: $tmp: ambiguous redirect
./pingscript: line 42: $tmp: ambiguous redirect

in relation to the following lines:
echo -e “To: $TO” > $tmp;
echo -e “Cc: $CC” >> $tmp;
echo -e “From: $FROM” >> $tmp;
echo -e “Content-Type: $CONTENTType”>>$tmp;
echo -e “MIME-Version: $MIMEVersion”>>$tmp;
echo -e “Subject: $SUBJECT”>>$tmp;
echo -e “Body: $BODY”>>$tmp;

Its not sending the email. I assume the redirects are the problem but i cant work out why, any ideas?


-------------

Pl@yer
That looks pretty cool, i haven't done any Perl so i will need to do some background reading before i can work out what its doing though :p
Is the html file the input and out file? does it simply append "up" or "down" to the end of the ip on each line

Regards
Paul

---

### Post by conneco on 2011-03-22
Hi paul

You dont happen to have the other half of the script do you? have you left it the same as in the original as it kinda depends on what value is held in $tmp variable

---

### Post by ratman99uk on 2011-03-22
> **conneco said:**
> Hi paul

You dont happen to have the other half of the script do you? have you left it the same as in the original as it kinda depends on what value is held in $tmp variable
for server in $(cat serverlist)
do
  ping -w 1 $server > /dev/null 2>&1
  if [ $? -eq 0 ] ; then
    echo "$server = running"
  else
    echo "$server = not running"

	    #!/usr/bin/ksh
	    #&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-
	    # Name: SendMail
	    # Purpose: To send mails using the sendmail command
	    # Usage: SendMail
	    # Owner: Ketan Joshi
	    # Setting: Just change the variables at the start of the script to
	    #          appropriate values. Create a message by modifying the string BODY
	    #          You can even have html tags in the body.
	    # Limitation: Currently, this does not support attachments.
	    #&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;
	    #Temporary file for containing the mail message
	    tmp=/tmp/mail-body-'date +%F';
	    touch $tmp && chmod 600 $tmp;
	    #Set up the various headers for sendmail to use
	    TO='user1@domain.com,user2@domain.com';
	    CC='';
	    FROM='administrator@domain.com';
	    SUBJECT='Server Down';
	    MIMEVersion='1.0';
	    CONTENTType="text/html; charset=us-ascii"
	    #Here write the content of your mail.
	    BODY="This is test mail. $server = not running";

	    echo Sending the mail.
	    echo -e "To: $TO" > $tmp;
	    echo -e "Cc: $CC" >> $tmp;
	    echo -e "From: $FROM" >> $tmp;
	    echo -e "Content-Type: $CONTENTType">>$tmp;
	    echo -e "MIME-Version: $MIMEVersion">>$tmp;
	    echo -e "Subject: $SUBJECT">>$tmp;
	    echo -e "Body: $BODY">>$tmp;

	    /usr/sbin/sendmail -t < $tmp;

	    rm -rf $tmp;
  fi
done

---

### Post by pl@yer on 2011-03-22
> **ratman99uk said:**
> Hi Guys

Pl@yer
That looks pretty cool, i haven't done any Perl so i will need to do some background reading before i can work out what its doing though :p
Is the html file the input and out file? does it simply append "up" or "down" to the end of the ip on each line

Regards
Paul

yep the html file is the input and output. 

It reads the file into an array then closes it. 

Opens the file again for writing and loops the through array.

Ping each member of arrays IP. 

If device is down it changes up to down on current line (if found), updates file and emails. 

If the device is up it changes down to up (if found).

I'll add some comments to the code.

---

### Post by ratman99uk on 2011-03-22
> **pl@yer said:**
> yep the html file is the input and output. 

It reads the file into an array then closes it. 

Opens the file again for writing and loops the through array.

Ping each member of arrays IP. 

If device is down it changes up to down on current line (if found), updates file and emails. 

If the device is up it changes down to up (if found).

I'll add some comments to the code.
some extra comments would be great. im leaving to go home in a bit so i will check in again tommorow.

Thanks again
Paul

---

### Post by pl@yer on 2011-03-22
```

#!/usr/bin/perl
#test ping results

#results of ping are stored in array @pingresult
#loop through array until finding "loss"
sub getpingresult () {
foreach my $curline (@pingresult){
chomp($curline);
if ($curline=~/loss/){
$pingres=$curline;
break;
};
};
};

#open input file load all lines into array @linearray
$inputfile="/var/www/test2/index.html";
open FHIN,"<$inputfile" or die $!;
@linearray=<FHIN>;
close FHIN;
#open input file for output 
open FHOUT,">$inputfile" or die $!;
#loop through members of @linearray (lines of file)
foreach $line (@linearray){
#split each line into an array delimiter is comma
#so we can get just the ip portion
@curip=split(/,/,$line);
$curip=$curip[0];
#load the results of ping request into @pingresult array
@pingresult=`/bin/ping -w 1 $curip`;
#run subroutine to parse results
& getpingresult;
#if the ping results found 100% for loss
if ($pingres=~/100%/){
#switch up to down if found
$line=~s/up/down/;
print FHOUT "$line";
`/usr/bin/mail -s "$curip is down" you@somewhere.com</dev/null`;
}
else {
#switch down to up if found
$line=~s/down/up/;
print FHOUT "$line";
}
}
close FHOUT

```

---

### Post by tgalati4 on 2011-03-22
I find it easier to use ruptime:

sudo apt-get install rwho
man ruptime

You can search the forum for ways to write a zenity or notify-osd script that displays up and down servers in your desktop toolbar.

Using zenity:

[http://ubuntuforums.org/showthread.php?t=328766&highlight=ruptime+zenity](http://ubuntuforums.org/showthread.php?t=328766&highlight=ruptime+zenity)

It could be rewritten for notify-osd.

---

### Post by pl@yer on 2011-03-22
Thanks for the zenety link it is on my list of things to check out.
ooh found a good link for zenity 
[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

---

### Post by conneco on 2011-03-22
I havnt looked at zenity but it defo sounds like the way forward, 

Regarding the shell script try running it in bin/bash rather than usr/bin/ksh

Ive never used korn shell so can't tell if the script would run

---

### Post by pl@yer on 2011-03-22
korn shell wont like substitution like this $() afaik I think you need to either use backticks `` or curly braces ${}

---

### Post by conneco on 2011-03-23
Hi made a script today while bored for pinging, hope it might help you on your way. I was planning on making it email but got to rush out.

```
#!/bin/bash
# Tool to ping a list of hosts and test if their responding.
clear

#holds the list of hosts to ping
hostList=(
www.google.co.uk 
192.168.0.1 
192.168.0.2 
192.168.0.3 
192.168.0.4 
192.168.0.5 
192.168.0.6 
192.168.0.7 
192.168.0.8 
192.168.0.9 
192.168.0.10
)

#Holds the up hosts that respond to the ping
upList=()

#Holds the list  of down hosts who dont respond to ping
downList=()

#Ping request time out 1= fast(but unreliable for non LAN use) recomend 5 for WAN pinging 
timeOut=1


#Ping every host in the list
for host in ${hostList[@]}
do
	STRC=`ping -W $timeOut -c 1 $host | grep "1 received" | cut -f5 -d ' '`
	if [ "$STRC" = "received," ]
	then
	echo $host reachable
	upList=( "${upList[@]}" $host )
		
	else
	echo $host unreachable
	downList=( "${downList[@]}" $host )	
	fi
done
echo

#Give a summary
echo Up:   ${upList[@]}
echo Down: ${downList[@]}

```

It will give you two arrays at the end with up hosts and down hosts so you should be able to use these lists to include in email

---

