---
title: "Fritzbox and mythutil --message"
date: 2012-04-05
forum: Mythbuntu
---

### Post by jcmiguel on 2012-04-05
I am working on a script that sends a message from backend to all frontends upon an incoming call. The script is working fine as I can test by starting from a command line. However, I got stuck in a very simple procedure. It is a perl script that should run after mythtv backend starts and before it stops. I don't know how to make it automatic and searches with init.d, rc.local and etc did not produced any solution. Could anyone help? 
PS: I will upload the script as soon as it is done. Right now I export the phonebook from fritzbox (as an xlm file), activate call monitor with #96*5* and access using port 1012. Any incoming call produces a frontend message with the phone number and the party that is calling (if it is on my phonebook) or the phone number. 
It saves us from answering a lousy call during CSI... lol

Here is the code:
#!/usr/bin/perl -w
# fritzbox_caller.pl 
# 
# --------------------------------------------------------------------------------------------
# Source code found @
# forums.slimdevices.com/showthread.php?93085-Fritz-Box-Call-Monitor/page2&p=699324#post699324
# forum.xbmc.org/showthread.php?pid=317793%23pid317793
# [www.wehavemorefun.de/fritzbox/index.php/Anrufmonitor_nutzen](www.wehavemorefun.de/fritzbox/index.php/Anrufmonitor_nutzen)
# 
# Modified by Joao Carlos Miguel
# 
# ------------------Preparing machines--------------------------------------------
# This code works on FRITZ!Box Fon WLAN 7270 v3 (fw 74.05.06)
# 	activate call monitor on fritzbox by dialing #96*5*
# 
# Backend running mythtv 0.25 and ubuntu 12.04 (3.2.0-22)
#	Create addressbook 	
#		Install  XML Treebuilder  with sudo apt-get install libxml-treebuilder-perl 
# 		Make directory addressbook with mkdir addressbook
# 		Export the phonebook from fritzbox with the name addressbook.xml
#		login via broswer and click >Telephony>Telephone Book>Save
# 		Change filename to addressbook.xml
# 		Place addressbook.xml on ~/addressbook
#
#
# --------------environmental settings---------------
#
use IO::Socket;
use strict;
use XML::TreeBuilder;
#
#
# --------- Initial configuration ---------#

my $FRITZBOX="fritz.box";#	your fritz box (ip or hostname)
my $PHONEBOOK="$ENV{HOME}/addressbook/addressbook.xml";#	location of addressbook
my $mythutilBCaddress="192.168.178.255";# mythutil broadcast address for your network
my $mythutilBCtimeout="10";# mythutil timeout

#-------- Connect to port 1012 of the fritzbox -------#

my $FB = new IO::Socket::INET (
        PeerAddr => $FRITZBOX,
        PeerPort => '1012',
        Proto => 'tcp'
        );
        die "Could not create socket: $!\n" unless $FB;

#-------read phonebook entries----------------#
sub read_book {
    my %book = ();
    my $file = "$PHONEBOOK";
    my $tree = XML::TreeBuilder->new();

    $tree->parse_file($file);
    foreach my $contact ($tree->find_by_tag_name('contact')) {
      foreach my $num ($contact->find_by_tag_name('number')) {
    	$book{$num->as_text}=$contact->find_by_tag_name('realName')->as_text . " - (" . $num->attr_get_i('type') . ")";
      }
    }

    return %book;
}


my %book = &read_book;


#-------------On ring gather callerID--------------#

while(<$FB>) {
	if ($_ =~ /RING/){
        	my @C = split(/;/);
 	    	my $SIP="";
		my $nr="";
                if (exists($book{$C[3]})) {
                    $nr=$book{$C[3]} . "  [". $C[3] ."]";
                } else {
                    $nr=$C[3];
                }
		my $mythmesg="";
		$mythmesg="'Incoming call from $nr'";
# --------------and finally broadcast it to your network...........
		system ("mythutil --message --message_text $mythmesg  --timeout $mythutilBCtimeout --bcastaddr $mythutilBCaddress\n");
		
	}
}

######################################################################################

---

### Post by Tsarunai on 2012-04-09
I don't know if this is what you're looking for but I've had trouble in the past with getting scripts to run on boot as well. I had made a simple script to watch a process and restart it if the process stopped. The problem I ran into was the loop in the script. Turns out the computer was waiting for the script to finish before it would finish booting. Seeing as it was built as an infinite loop, it was never going to finish and therefore the machine would never boot. I did some hunting around and finally got it working by creating a file in the rc3.d directory. This should also work with rc.local. 

The file was one line:

/absolute/path/tofile.sh &

The ampersand ran the script as a background process and allowed the computer to finish booting. This won't help with running the script before the backend stops though. It does look like it runs until someone calls, then ends. If that's the case, then the infinite loop will restart it once it's been triggered (same as I did on the other server) by adding the above line to the end of the script.

I could be reading the script entirely wrong though. I checked the website in the script but don't know german. Hope it helps.

---

### Post by nickrout on 2012-04-09
> **jcmiguel said:**
> I am working on a script that sends a message from backend to all frontends upon an incoming call. The script is working fine as I can test by starting from a command line. However, I got stuck in a very simple procedure. It is a perl script that should run after mythtv backend starts and before it stops. I don't know how to make it automatic and searches with init.d, rc.local and etc did not produced any solution. Could anyone help? 
PS: I will upload the script as soon as it is done. Right now I export the phonebook from fritzbox (as an xlm file), activate call monitor with #96*5* and access using port 1012. Any incoming call produces a frontend message with the phone number and the party that is calling (if it is on my phonebook) or the phone number. 
It saves us from answering a lousy call during CSI... lol

Here is the code:
#!/usr/bin/perl -w
# fritzbox_caller.pl 
# 
# --------------------------------------------------------------------------------------------
# Source code found @
# forums.slimdevices.com/showthread.php?93085-Fritz-Box-Call-Monitor/page2&p=699324#post699324
# forum.xbmc.org/showthread.php?pid=317793%23pid317793
# [www.wehavemorefun.de/fritzbox/index.php/Anrufmonitor_nutzen](www.wehavemorefun.de/fritzbox/index.php/Anrufmonitor_nutzen)
# 
# Modified by Joao Carlos Miguel
# 
# ------------------Preparing machines--------------------------------------------
# This code works on FRITZ!Box Fon WLAN 7270 v3 (fw 74.05.06)
# 	activate call monitor on fritzbox by dialing #96*5*
# 
# Backend running mythtv 0.25 and ubuntu 12.04 (3.2.0-22)
#	Create addressbook 	
#		Install  XML Treebuilder  with sudo apt-get install libxml-treebuilder-perl 
# 		Make directory addressbook with mkdir addressbook
# 		Export the phonebook from fritzbox with the name addressbook.xml
#		login via broswer and click >Telephony>Telephone Book>Save
# 		Change filename to addressbook.xml
# 		Place addressbook.xml on ~/addressbook
#
#
# --------------environmental settings---------------
#
use IO::Socket;
use strict;
use XML::TreeBuilder;
#
#
# --------- Initial configuration ---------#

my $FRITZBOX="fritz.box";#	your fritz box (ip or hostname)
my $PHONEBOOK="$ENV{HOME}/addressbook/addressbook.xml";#	location of addressbook
my $mythutilBCaddress="192.168.178.255";# mythutil broadcast address for your network
my $mythutilBCtimeout="10";# mythutil timeout

#-------- Connect to port 1012 of the fritzbox -------#

my $FB = new IO::Socket::INET (
        PeerAddr => $FRITZBOX,
        PeerPort => '1012',
        Proto => 'tcp'
        );
        die "Could not create socket: $!\n" unless $FB;

#-------read phonebook entries----------------#
sub read_book {
    my %book = ();
    my $file = "$PHONEBOOK";
    my $tree = XML::TreeBuilder->new();

    $tree->parse_file($file);
    foreach my $contact ($tree->find_by_tag_name('contact')) {
      foreach my $num ($contact->find_by_tag_name('number')) {
    	$book{$num->as_text}=$contact->find_by_tag_name('realName')->as_text . " - (" . $num->attr_get_i('type') . ")";
      }
    }

    return %book;
}


my %book = &read_book;


#-------------On ring gather callerID--------------#

while(<$FB>) {
	if ($_ =~ /RING/){
        	my @C = split(/;/);
 	    	my $SIP="";
		my $nr="";
                if (exists($book{$C[3]})) {
                    $nr=$book{$C[3]} . "  [". $C[3] ."]";
                } else {
                    $nr=$C[3];
                }
		my $mythmesg="";
		$mythmesg="'Incoming call from $nr'";
# --------------and finally broadcast it to your network...........
		system ("mythutil --message --message_text $mythmesg  --timeout $mythutilBCtimeout --bcastaddr $mythutilBCaddress\n");
		
	}
}

######################################################################################

You need to start it as a daemon with a proper startup script in /etc/init.d, or a upstart script. Set it to start and stop in the right order in the usual way.

---

