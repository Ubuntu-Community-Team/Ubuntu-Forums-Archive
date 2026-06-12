---
title: "Deleting channels from Backend"
date: 2014-11-29
forum: Mythbuntu
---

### Post by hollywoodpete on 2014-11-29
I have a HDHomeRun Prime and Duel running fine with My Mythbuntu Backend. It shows over 600 channels on my XBMC frontends. I would like to view only the HD channels and delete the PPV, Music Chanels, Non-functional sport channels ect. I tried the Web interface, checked the delete boxes and hit save but the channels simply came back. I tried going to the Channel Manager on the Backend and hit "D" and deleted the channels but after closing the channels re-appeared. Is there a way to view only high def channels or permanently delete the unwanted channels?

---

### Post by khPWXxF on 2014-12-01
It will work if you hide the channels.

Do you fancy being a guinea pig?

I have some code to do this in bulk - only tested on my system though.  I had hoped to use the new api interface for both getting channel information from the database (which it does) and for rewriting the 'hidden' field but the latter has me stumped so I use direct dbase code which I scrounged from elsewhere.

I tried other routines but they needed a complete list of chanels to include/exclude - choosing those which include text in the name is much more powerful. 
 
Download both these files, put them in same directory, then chmod +x them

It has a UK bias - alter @keep and @discard to suite your channel lineup.  Just put channel name fragments to include or exclude whole tranches of them ('adult' and 'shop' in @discard are good ones!).  Once you have a good set you can then reuse the code whenever your channel lineup changes.  
 
Also, change the  open CONFIG line to point it at the xml file holding your credentials.

Then, ./edit_channels.pl
You can add extra channels manually once the program is running.  When you are happy with your selection let it rip.

Just make sure you have a good database backup before you start and please give feedback!

Phil
 
edit_channels.pl

```
#!/usr/bin/perl -w
use strict;
use scan_database;
use LWP::UserAgent;  # needs 'sudo apt-get install libwww-perl'


#Show channels with these strings in their names:
my @keep =('bbc','itv','channel');


#and hide these:
my @discard=('adult','rocks','create','qvc','television x','jewellery',
'store','gems','travel','red button','bbc rb','quest','food network','ideal world',
'pop','kerrang!','kiss','pick','tru','really','4music','viva','tbn','jazeera');


#-----------------------------


my $backend;
my $mysqluser=''; my $mysqlpwd='';


#get database credentials


open CONFIG, "</home/phil/.mythtv/config.xml" or die"Cannot open config.xml $!";
my $temp=0;
while ($_ = <CONFIG>){
    if (m!<UserName>(\S+)</UserName>!) {$mysqluser=$1; $temp +=1};
    if (m!<Password>(\S+)</Password>!) {$mysqlpwd=$1; $temp +=10};
    if (m!<Host>(\S+)</Host>!) {$backend=$1; $temp +=100};
}
close CONFIG;
if ($temp != 111){die "Host/Username/Password not extracted from config.xml"};


print "Extracted host $backend, database user $mysqluser & sql password $mysqlpwd\n";
&more;


my %sources; my $videosource; my %header;




#check compatibility


GetDBheader(\%header, $backend,'VideoSourceList');
$_= $header{'Version'};
print "\nBackend version is $_\n";
unless (/^0.27./){&check('Program only validated against 0.27.  Continue anyway')};  






#which video source?


GetDBinfo(\%sources, $backend,'VideoSourceList','','Id', 'SourceName');
do{
    print "\nVideo sources are\n";
    foreach (keys %sources){
        print "$_  $sources{$_}{'SourceName'}\n";
    }
    print "Which video source? ";
    chomp ($videosource=<STDIN>);
} while (!defined $sources{$videosource});


my %mydata;


#get list of channels into hash indexed by channel name.
&scan_database::GetDBinfo(\%mydata, $backend, 'GetChannelInfoList',"SourceID=$videosource", 'ChannelName','ChanNum','Visible');


#create 'new visibile' item
foreach (keys %mydata){
    $mydata{$_}{'NewVisible'} =  $mydata{$_}{'Visible'};
}
 
#mark keeps
my $tag;
foreach $tag (@keep){
    foreach (keys (%mydata)){
        $mydata{$_}{'NewVisible'}='true' if (/$tag/i);
    }
}


#mark discards
foreach $tag (@discard){
    foreach (keys (%mydata)){
        $mydata{$_}{'NewVisible'}='false' if (/$tag/i);
    }
}




#show contents as check
&showchannels;


#decide which need to change
my @hide; my @unhide;
foreach $_ (sort keys (%mydata)){
    if ($mydata{$_}{'NewVisible'} ne $mydata{$_}{'Visible'}){
        #this channel has been changed
        if ($mydata{$_}{'NewVisible'} eq 'true'){
            push @unhide, $mydata{$_}{'ChanNum'};
        }else{
            push @hide, $mydata{$_}{'ChanNum'};
        }
    }
}
printf "%4d channels to hide:\n", $#hide+1;
printf "%4d channels to unhide:\n", $#unhide+1;
if ($#unhide + $#hide +2 <=0){print "No changes needed\n"; exit 0};


&more;


my ($selection,$selection2,$i);


print "Will run mysql statements:\n";
if ($#unhide>-1){
    $selection = "update channel set visible=1 where channum=$unhide[0]";
    for $i (1..$#unhide){ $selection .= " or channum=$unhide[$i]"};
    $selection .=';'; 
    print "$selection\n\n";
}


if ($#hide>-1){
    $selection2 = "update channel set visible=0 where channum=$hide[0]"; 
    for $i (1..$#hide){ $selection2 .= " or channum=$hide[$i]"};
    $selection2 .=';';
    print "$selection2\n\n"; 
}


&check('Continue and change database');
&check('Do you have a good backup');
&check('Last chance - ok to change database');




#cribbed stuff here  ===============
#would prefer to use API but this bit undocumented.
use DBI;


my $dsn; my $sth; my $dbh;
$dsn="DBI:mysql:database=mythconverg;host=$backend";
$dbh=DBI->connect($dsn, $mysqluser, $mysqlpwd, { PrintError=>1, RaiseError=>1 } );
$dbh->{RaiseError} = 0; # only warn on DB errors from here


if ($#hide>-1) {$sth=$dbh->prepare("$selection2")};
if ($#unhide>-1) {$sth=$dbh->prepare("$selection")};
$sth->execute();
$sth->finish();
$dbh->disconnect();


print "All done!\n";
exit 0;


#---------------
sub check{
    while (1){
        print "$_[0]? (answer yes or no)\n";
        $_=<STDIN>;
        chomp;
        if (/^yes$/i){return};
         if (/^no$/i){exit 0};
    }
}
#----------------
sub more{
    print "press return to continue:";
    <STDIN>;
}
#---------------
sub showchannels{
#&scan_database::GetDBinfo(\%mydata, $backend, 'GetChannelInfoList','', #'ChannelName','ChanNum','Visible');


    my @list;
    my $reply=0;
    my $ok=0;
    while (1){
        $ok=0;
        print "\nPlease reply:\n";
        print " 1 to show channels by name\n";
        print " 2 to show channels by number\n";
        print " 3 to show channels by wanted\n";
        print " 4 to mark channels as not wanted\n";
        print " 5 to mark channels as wanted\n";
        print " 6 to continue and update database\n";
        print " 7 to quit\n";
        chomp ($reply=<STDIN>);


        if ($reply eq '7'){exit 0};
        if ($reply eq '6'){return 0};
        if ($reply eq '5'){&ManualHides('true') ;next};
        if ($reply eq '4'){&ManualHides('false') ;next};


        if ($reply eq '3'){$ok=1;
                @list=sort {($mydata{$a}{'NewVisible'} cmp $mydata{$b}{'NewVisible'}) or
                             ($mydata{$a}{'ChanNum'} <=> $mydata{$b}{'ChanNum'})} keys (%mydata)};
        if ($reply eq '2'){$ok=1;
            @list=sort {$mydata{$a}{'ChanNum'} <=> $mydata{$b}{'ChanNum'}} keys (%mydata)};
        if ($reply eq '1'){$ok=1; @list=sort {lc($a) cmp lc($b)} keys (%mydata)};
        if ($ok ==0){next};


        my $count=0;
        foreach $_ (@list){
            if ($count==0){
                print "\n\nName                   Number        Wanted?\n";
                print "--------------------------------------------\n";
            }
            printf "%-25s %-5s      %-7s\n", $_, $mydata{$_}{'ChanNum'}, $mydata{$_}{'NewVisible'} ;
            $count++;
            if ($count==25){$count=0; &more};
        }
        &more;
    }
}
sub ManualHides{
    my $newstate=$_[0];
    print "Give a string to be found in names of channels to be selected (case insensitive): ";
    chomp(my $tag=<STDIN>);
    $tag=lc($tag);
    foreach (keys (%mydata)){
        if (/$tag/i){$mydata{$_}{'NewVisible'}=$newstate} ;
    }
}



```


scan_database.pm
```
package scan_database;

use strict;
use Exporter;
use LWP::UserAgent;  # needs 'sudo apt-get install libwww-perl'

our $VERSION     = 1.00;
our @ISA         = qw(Exporter);
our @EXPORT      = qw(GetDBinfo GetDBheader);
our @EXPORT_OK   = qw($url_buffer);

my $url_buffer;
my $counter;
my $hostopened='';
my $browser;

#Extract data from database
#  Routine GetDBinfo
# params are:
#   reference to hash to fill
#   IP of host
#   Catagory required eg GetRecordedList
#   extra infor to go in call (if any).
#   required hash key
#   list of things to extract
#   eg :-
#   GetDBinfo(\%mydata, '192.168.1.67', 'GetRecordedList', '',
#    'FileName','Title', 'LastModified');
#  If key or extracted name is # then this is replaced by a counter.

#routine GetDBheader
# params are:
#   reference to hash to fill
#   IP of host
#   Catagory required eg GetRecordedList
#   extra info to go in call (if any).
#  eg GetDBheader(\%mydata, '192.168.1.67','getrecordedlist','');



my %steer = (
    getchannelinfolist  => ['Channel/GetChannelInfoList', 'ChannelInfo','ChannelInfos'],
    getrecordedlist     => ['Dvr/GetRecordedList?Descending=true', 'Program','Programs'],
    videosourcelist     => ['Channel/VideoSourceList', 'VideoSource','VideoSources'],
    #add more like this => [url, separator for getDBinfo, separator for getDBheader], 
);
#------------
sub GetDBheader{
    my ($hashref, $ip_addr, $class,$extra)=@_;
    $class=lc $class;
    unless (defined ($steer{$class})) {die "Sorry - $class not supported"};
    $counter=0;
    #read from backend
    &ReadBackend($ip_addr, $class, '');

    ($url_buffer)= split /<$steer{$class}[2]>/, $url_buffer;
    my @bits = split /></, $url_buffer.'<';
    foreach (@bits){
        if (m!</!){
            (my $key,$_)=split />/, $_;
            (my $value)=split /</,$_;
            #print "$key = $value\n";
            $$hashref{$key}=$value;
            $counter++;
        }
    }
    return $counter;
}
#-----------------------------
sub ReadBackend{
    my ($ip_addr, $class, $extra)=@_;
    unless ($hostopened eq $ip_addr){
        $browser = LWP::UserAgent->new;
        $browser->timeout(10);
        $hostopened = $ip_addr;
    }
   
    my $command="http://$ip_addr:6544/$steer{$class}[0]";
    if ($extra){
        if ($command =~ /\?/){
            $command .= '&' . $extra;
        }else{
            $command .= '?' . $extra;
        }
    }

    my $response = $browser->get($command);
    unless($response->is_success){
        die 'Cannot connect to backend. Bad address?  Not running?'};
    $url_buffer = $response -> content;
}

#---------------------------
sub GetDBinfo{

my ($hashref, $ip_addr, $class, $extra, $key_name, @params)=@_;

    $class=lc $class;
    unless (defined ($steer{$class})) {die "Sorry - $class not supported"};
 
    #read from backend
    &ReadBackend($ip_addr, $class, $extra);
   
    $counter=0;
    my $base=index($url_buffer, "<$steer{$class}[1]>");
    while ($base>-1){
        &ProcessRecording($hashref, $base, $key_name, @params);
        $base=index($url_buffer, "<$steer{$class}[1]>", $base+10);
        $counter++;
    }
    return $counter;
}
#---------------
sub ProcessRecording{
    #strip interesting data from record
    my ($hashref, $start_at, $key_name, @params) = @_;

    my $index=$counter;
    if ($key_name ne '#'){ $index=&getparameter($key_name,$start_at)};

    foreach (@params){
        if (/^#$/){
            $$hashref{$index}{$_}=$counter;
        }else{
            $$hashref{$index}{$_}=&getparameter($_, $start_at);
        }
    }
}
#-------------------------
sub getparameter{

my ($param, $base) = @_;

        my $start= index($url_buffer, "<$param>",$base);
        if ($start<0){die "cannot find $param in record"};

        $start=$start + length($param) +2;
       
        my $end=index($url_buffer, "</$param>", $start);
       
        my $data=substr $url_buffer, $start, $end-$start;
        $data =~ s/&amp;/&/g;
        $data;
}
1;

```

---

### Post by hollywoodpete on 2014-12-01
Thanks khPWXxF,
I would love to help out but my wife's patience is wearing thin. I have my system usable for her at the moment but a catastrophic issue may cause her to meltdown. I am slowly tweaking the system. I also am not sure I have the knowledge to successfully make the changes you suggested anyway. I am better at checking boxes in a GUI

---

### Post by khPWXxF on 2014-12-01
It's all pretty innocuous up until the 'last chance'.   However, I respect and understand your dilemma.
If you want to stick with gui then mark them as hidden in backend setup > channel editor rather than deleting them.
Phil

---

### Post by hollywoodpete on 2014-12-01
> **khPWXxF said:**
> It's all pretty innocuous up until the 'last chance'.   However, I respect and understand your dilemma.
If you want to stick with gui then mark them as hidden in backend setup > channel editor rather than deleting them.
Phil


Thanks for the help. I will hide them on the backend. I'm at work now but don't remember seeing an option to hide them on the Channel Manager page. I will look again. I did see a post about commenting them out in the SQL database which sounds like a good option. Just not sure where to find the channels listed

---

### Post by Lester_Burnham on 2014-12-02
Hi,

Adding another method.
You can also hide them using mythweb.
[http://backend_ip/mythweb/settings/tv/channels](http://backend_ip/mythweb/settings/tv/channels)

Go to settings>tv>channels or copy and paste the above with your backend_ip address.  Look for the visible checkbox column, un-tick the ones you DON'T want and hit save.

Lester

---

### Post by hollywoodpete on 2014-12-03
> **Lester_Burnham said:**
> Hi,

Adding another method.
You can also hide them using mythweb.
[http://backend_ip/mythweb/settings/tv/channels](http://backend_ip/mythweb/settings/tv/channels)

Go to settings>tv>channels or copy and paste the above with your backend_ip address.  Look for the visible checkbox column, un-tick the ones you DON'T want and hit save.

Lester

Thanks, this looks like a good answer. I tried checking the delete box and hit save but they just pop up again. I hid a bunch on the backend this morning with the Channel Manager but it was very time consuming and my fingers were getting sore from hitting the Tab button repeatedly. I did try hiding them with the mythweb GUI and it is much easier. Unfortunately the ones I hid with the GUI still showed up on the frontends when I did a quick check while the ones hidden on the backend were hidden. The boxes of the ones I hid on the backend were hidden on the mythweb GUI along with the ones I tried to hide with the GUI  . I may have to stop and restart the backend for this to work?

---

### Post by Lester_Burnham on 2014-12-03
Hi,
Maybe they're continually being updated by your listings source.

Might need someone familiar with the engine room in mythtv :)
Lester

---

### Post by hollywoodpete on 2014-12-06
> **Lester_Burnham said:**
> Hi,
Maybe they're continually being updated by your listings source.

Might need someone familiar with the engine room in mythtv :)
Lester


Yes, they appear to be re-added by Data Direct. If there was a way I could stop that from happening, I might be better off. MythWeb GUI does not seem to work. I tried hiding the un-wanted channels (unchecking the visible box) clicked save, screen refreshes and the checks come back. The only way I have found that seems to hide them is going into each channel individually on the backend. It has been very time consuming and I have a lot more channels to go

---

### Post by hollywoodpete on 2014-12-07
Well I thought I had this solved. I logged in to Schedules Direct and edited my channel line up. By simply hitting the edit box, clicking on the channels I didn't want (they turned white with a line through them) and then clicked save. Logged out and then back in to make sure the change was persistent. I went to the backend and then deleted all of the channels I didn't want. I logged out and then restarted the server. Amazingly all of the channels I had hidden and delete reappeared on my frontend. I checked mythweb and all of the visible boxes that were previously unchecked, had checks. Odd

---

### Post by Lester_Burnham on 2014-12-07
Hi,

If you look at the mythfilldatabase options on [this page]("https://www.mythtv.org/wiki/Mythfilldatabase#Command_line_options"), you'll see lots of options for DataDirect.
Especially channel list options.
--remove-new-channels           disable new channels on datadirect web interface

Here is a snippet from a [mailing list]("https://www.mythtv.org/pipermail/mythtv-users/2010-April/286521.html"). Probably an older version, but a better explanation.
> --remove-new-channels
   When using DataDirect, ask mythfilldatabase to
   remove new channels (those not in the database)
   from the DataDirect lineup.  These channels are
   removed from the lineup as if you had done so
   via the DataDirect website's Lineup Wizard, but
   may be re-added manually and incorporated into
   MythTV by running mythfilldatabase without this
   option.  New channels are automatically removed
   for DVB and HDTV sources that use DataDirect.

So, can you remove them from the "lineup Wizard" on DataDirect?

Lester

---

### Post by hollywoodpete on 2014-12-11
> **Lester_Burnham said:**
> Hi,

If you look at the mythfilldatabase options on [this page]("https://www.mythtv.org/wiki/Mythfilldatabase#Command_line_options"), you'll see lots of options for DataDirect.
Especially channel list options.
--remove-new-channels           disable new channels on datadirect web interface

Here is a snippet from a [mailing list]("https://www.mythtv.org/pipermail/mythtv-users/2010-April/286521.html"). Probably an older version, but a better explanation.


So, can you remove them from the "lineup Wizard" on DataDirect?

Lester

FWIW, I have finally decided to give up. The new version of XBMC (Kodi) which I use as most of my frontends allows me to create a favorite list of channels and add the appropriate Icons. I may go back at a later date and try this again but for now, everything is usable

---

### Post by Senkoboy on 2015-01-19
> **hollywoodpete said:**
> Well I thought I had this solved. I logged in to Schedules Direct and edited my channel line up. By simply hitting the edit box, clicking on the channels I didn't want (they turned white with a line through them) and then clicked save. Logged out and then back in to make sure the change was persistent. I went to the backend and then deleted all of the channels I didn't want. I logged out and then restarted the server. Amazingly all of the channels I had hidden and delete reappeared on my frontend. I checked mythweb and all of the visible boxes that were previously unchecked, had checks. Odd

I had the same problem. My fix was: I went to Schedules Direct and edited my channel line up. Went to the backend and deleted the old source, added a new source, (the edited Schedules Direct lineup) and tied the new source to my HD Homerun box.  This was the 1st time I had tried the downloaded the channel lineup, in the past I had always scanned for my channels.

---

### Post by hollywoodpete on 2015-03-08
well after several months I finally figured out how to get MythWeb to delete or hide (uncheck visible). The problem was in my php.ini file. I found some help here [http://lists.mythtv.org/pipermail/mythtv-users/2014-July/365893.html](http://lists.mythtv.org/pipermail/mythtv-users/2014-July/365893.html)   I still had to figure out where the php.ini file was located. It turns out it was here /etc/php5/apache2/php.ini. I had to uncomment
max_input_vars = 1000
and then change the value to 100000
save and restart
After that change, MythWeb will delete and allow me to uncheck the visible box

---

