---
title: "SSA to SRT"
date: 2009-06-21
forum: Multimedia Software
---

### Post by Qchan on 2009-06-21
[b][color=darkred]
Sure, there are many programs that can do this, but they are mostly all GUI based. I know a lot of people have been looking for something they can use on the command line. I finally found the script and figured I'd share it with people.

It's under the GNU license, but just happened to be in Chinese. I translated it using Google's translator. I checked the code and everything works out pretty well.

If you have any problems with it, let me know. I have the original Chinese version.

As for the original link, I'm not sure. I had a hard time finding it, so I honestly can't remember the original link. Sorry :/
[/b][/color]

[PHP]
#!/usr/bin/perl -w

use strict;

use encoding 'utf-8';

use Getopt::Long;

use File::Spec;



Getopt::Long::Configure( "pass_through", "no_ignore_case" );



# Default encoding
my $defaultEnc  = 'utf8';

my $fromEnc     = '';

my $toEnc       = '';

my $help        = 0;

my $preserve    = 0;

my $combine     = 0;

my $showVer     = 0;

my $showLicense = 0;

my $dosFormat   = 0;

my $macFormat   = 0;



my $oldTime = "";



$fromEnc = $ENV{'ASS2SRT_FROM'};

$toEnc   = $ENV{'ASS2SRT_TO'};



GetOptions(

    "help|h",     \$help,      "from|f=s",    \$fromEnc,

    "to|t=s",     \$toEnc,     "default|d=s", \$defaultEnc,

    "preserve|p", \$preserve,  "combine|c",   \$combine,

    "version|v",  \$showVer,   "dos|o",       \$dosFormat,

    "mac|m",      \$macFormat, "license|l",   \$showLicense

);



# Wrap format
my $crlf = "\n";



# If the specified output at the same time as Mac and DOS format, responding to an error message and the end of
( $dosFormat && $macFormat )

    && die( "\n&#37679;&#35492;: \n\t&#36984;&#38917; -m|--mac &#33287; -o|--dos &#19981;&#21487;&#21516;&#26178;&#23384;&#22312; \n" );



if ($dosFormat) { $crlf = "\r" . $crlf; }

if ($macFormat) { $crlf = "\r"; }



# Program version

my $version = "0.2.4.2";



# Display help message

if ($help) { usage(); }



# Show license information

if ($showLicense) { license(); }



# Show version of the message
if ($showVer) { showVersion(); }



# Source file encoding is not specified, the set with the same defaultEnc
if ( !$fromEnc ) { $fromEnc = $defaultEnc; }



# Do not specify the purpose of file encoding, the set with the same defaultEnc
if ( !$toEnc ) { $toEnc = $defaultEnc; }



#. *** file file name
my $assFile = shift || '';

if ( !$assFile ) { usage(); }



#. Srt file file name, the default value. *** file name, but changed the name extension. Srt

my $srtFile = shift || '';

if ( !$srtFile ) {

    $srtFile = $assFile;

    $srtFile =~ s|\.[^.]*$||;

    $srtFile .= ".srt";

}



# Using the parameters listed
print "Using parameters: \n";

print "\t .*** File Encoding: $fromEnc\n";

print "\t .SRT File Encoding: $toEnc\n";

print "\n";



# Open file
open( ASSFILE, "<", $assFile )

    or die 'Can not open ".***" the source file&#65306;' . $assFile . ", please check!&#65281;\n";

open( SRTFILE, ">", $srtFile )

    or die 'Can not open ".srt" The purpose of file&#65306;' . $srtFile . ", please check!\n";



# Specify the file encoding

binmode( ASSFILE, ':encoding(' . $fromEnc . ')' );



# Check the existence of the system environment variable OS (Windows should be)
my $OS_TYPE = $ENV{'OS'};



# Assigned to write the encoded file using the string set

my $toEncString = ':encoding(' . $toEnc . ')';



# Depending on OS type (only for Windows) file amendments to open coding

if ( $OS_TYPE && $OS_TYPE =~ m/windows/i ) {

    print "Operation System is: " . $OS_TYPE

        . ", Checking File Encoding... \n";



    # Only use UTF16 or UCS format when otherwise specified (other test)

    if ( ( $toEnc =~ m/utf16/i ) || ( $toEnc =~ m/ucs/i ) ) {

        $toEncString = ':raw' . $toEncString;

    }

}



# Specified file used to write code

binmode( SRTFILE, $toEncString );



# Windows on Unicode output file identification mark to join the BOM

if ( $toEncString =~ m/:raw/i ) {

    print SRTFILE "\x{FEFF}";

    print "Using unicode encoding, print BOM signature to file: " . $srtFile

        . "\n\n";

}



# Number of records subtitles

my $line = 0;



# Read. *** and deal with the source file
while (<ASSFILE>) {

    chomp;



    # If Dialougue in the beginning, the setting for the subtitles
    if (m/^Dialogue:/) {

        $line = writeSrt( $line, $_ );



    # If the beginning Title or Original, the source for the subtitles
    }

    elsif (m/^(Title:|Original)/) {

        print $_ . "\n";

    }



}



# Close the file

close ASSFILE;

close SRTFILE;



# Write. Srt file

sub writeSrt {



    # Deal with the number of rows

    my $line = $_[0];



    # From. *** of the original content

    my $content = $_[1];



    my $begin;

    my $end;

    my $subtitle;

    my $currentTime;



    # Solved starting time, ending time, subtitle format, subtitles content

    if ( $content

        =~ m/Dialogue: [^,]*,([^,]*),([^,]*),([^,]*),[^,]*,[^,]*,[^,]*,[^,]*,[^,]*,(.*)$/

        )

    {

        $begin    = $1;

        $end      = $2;

        $subtitle = $4;



        my $isComment = $3;



        # the separator between seconds and ms is "," -- not ".", so we change it !

        $begin =~ s/\./\,/g;

        $end   =~ s/\./\,/g;



        # If the time format will not be part of the hour when the two yards, make up two yards
        if ( $begin =~ m/^\d{1}:/ ) {

            $begin = "0" . $begin;

        }



        if ( $end =~ m/^\d{1}:/ ) {

            $end = "0" . $end;

        }



        # First filter out the end of every title to the digital sign in order to follow-up to the output under a variety of formats on different platforms

        $subtitle =~ s/\r$//g;



        # If there is no such setting. *** control commands, then filter out the

        if ( !$preserve ) {

            $subtitle =~ s/\{\\[^}]*\}//g;

        }



        # Comment if the subtitle format, then in the before and after the add ()
        if ( $isComment eq 'comment' ) {

            $subtitle = '(' . $subtitle . ')';

        }



        # Write. Srt file
         # Because. *** unit of time (10ms) with. Srt (1ms), so the full complement of 0
        $currentTime = $begin . "0 --> " . $end . "0";



        $subtitle =~ s/\\N/$crlf/g;



        # Timeline combined output mode
        if ($combine) {



            if ( $oldTime eq $currentTime ) {

                print SRTFILE $subtitle;

            }

            else {

                $line++;

                if ( $line > 0 ) {

                    print SRTFILE $crlf . $crlf . $crlf . $line . $crlf;

                }

                else {

                    print SRTFILE $line . $crlf;

                }

                print SRTFILE $currentTime . $crlf;

                print SRTFILE $subtitle;

            }

            $oldTime = $currentTime;

        }

        else {

            # The general output model

            $line++;

            print SRTFILE $line . $crlf;

            print SRTFILE $currentTime . $crlf;

            print SRTFILE "$subtitle " . $crlf . $crlf . $crlf;

        }



        return $line;

    }

}



# Use

sub usage {

    print <<__HELP__;



ass2srt [option] .*** source files [.srt purpose of file]



    The Advanced SubStation Alpha ".***" file format to SubRip ".srt" format. 



Options:
  -h --help               help show this help message

    

  -d, --default=encoding  default = encoding set the default file encoding, which is the purpose of the source file and use the same code file.

                          The default value is UTF-8 encoding format.
                                     

  -f, --from=encoding    from = encoding specified source file. *** coding system used. The set will be covered by the aforementioned pre -
                           Coding based on the settings file, when not specified the default file encoding for the default value.
                        &#8251; You can also use the system environment variables specified ASS2SRT_FROM
                                

  -t, --to=encoding       encoding file specified purposes. srt coding system used. The set will be covered by the aforementioned pre -
                           Coding based on the settings file, when not specified the default file encoding for the default value.
                        &#8251; You can also use the system environment variables specified ASS2SRT_TO



  -p, --preserve          preserve the source file to retain. *** subtitles in the control instructions, write together. srt file.


  -c, --combine	          combine the same number of merge subtitles timeline set by the content under a single timeline.
  

  -o, --dos               dos specified output file format for DOS (the default format for Unix)
                        &#8251; At the same time can not be set -m/--mac
  

  -m, --mac               mac specify the output file format for the Mac (the default format for Unix)
                        &#8251; At the same time can not be set -o/--dos


.*** source file:

    &#31526;&#21512; Advanced SubStation Alpha (.***) &#25110; SubStation Alpha (.ssa) &#26684;&#24335;

    Subtitles of the original file.


[.srt purpose file]&#65306;

   SubRip default output file format for the purpose of file name, the default value. *** the same source file,

     However, extension changed to. Srt.


Operation Example:



 1. Unicode/UTF-16 LE will be encoded. *** into the source file to Big5 encoding. Srt purpose file

  

       myhost \ $ perl ass2srt.pl-f utf16-le-t big5 utf16-le.*** big5.srt

      

   2. Big5 encoding. *** into the source file to UTF-8 encoded. Srt purpose file

    

       myhost \ $ perl ass2srt.pl-f big5-t utf8 big5.*** utf8.srt

      

   3. To be UTF-8 encoded. *** into the source file to UTF-8 encoded. Srt purpose file

  

       myhost \ $ perl ass2srt.pl utf-8.*** utf-8.srt

      

   4. UCS-2LE encoding. *** source file into the UCS-2LE encoding. Srt purpose file

  

       myhost \ $ perl ass2srt.pl-f ucs-2le-t ucs-2le ucs-2le.*** ucs-2le.srt

      

   5. Through the environment variables specified encoding type

      &#8251; Do not some of the operating system settings before and after the words "or 'quotation marks
  

     myhost \ $ export ASS2SRT_FROM = utf16-le

       myhost \ $ export ASS2SRT_TO = big5

       myhost \ $ perl ass2srt.pl utf16-le.*** big5.srt                              



__HELP__

    exit 2;

}



# Show version of the message

sub showVersion {



    print <<__VERSION__;



ass2srt $version - Convert subtitles from .*** to .srt format

	

  Advanced SubStation Alpha subtitle file format conversion tool

  (c) 2006 Ada Hsu, hungwei.hsu (at) gmail (dot) com



__VERSION__

    exit 2;

}



# &#36575;&#39636;&#25480;&#27402;

sub license {



    print <<__LICENSE__;



  ass2srt $version - Convert subtitles from .*** to .srt format



  Advanced SubStation Alpha subtitle file format conversion tool

  (c) 2006 Ada Hsu, hungwei.hsu (at) gmail (dot) com

  

 The use of the software CC-GNU GPL (http://creativecommons.org/licenses/GPL/2.0/) authorization,

   You can view the relevant provisions of http://www.gnu.org/copyleft/gpl.html text.

  

   You are free to use the software, but software maintenance personnel will not use the software created by the software and hardware

   Physical injury or loss of any responsibility.


__LICENSE__

    exit 2;



}
[/PHP]

---

### Post by Skylark13 on 2009-08-25
> **Qchan said:**
> [B][COLOR=darkred]
Sure, there are many programs that can do this, but they are mostly all GUI based. I know a lot of people have been looking for something they can use on the command line. I finally found the script and figured I'd share it with people.[/COLOR][/B]
Thanks a lot for this, it was just what I was looking for.

I added some error correction so that timing errors could be automatically fixed. For example I had some subtitles where one subtitle started before the previous one ended. Presumably this is ok for .*** subtitles, it just keeps the previous subtitle on screen and puts the new one below it, but in .srt subtitles it's an error and mp4box for example complains about it, tries to correct it and in my case, crashed. So I added correction directly in the script. I've attached the new code to this post (just remove the .txt extension, the forum doesn't allow upload of .pl files).

I compared the output of this new ass2srt.pl with what DSRT ([http://dsrt.boom.ru/](http://dsrt.boom.ru/)) gives with its error correction on the same script (Ctrl-F7) and the output is identical (even down to the newlines and everything). So the results are good.

(I'll try to contact the original author to give him the modified code - it would also be nice to get a real translation of the comments and usage text since it's pretty bad...)
[B][COLOR=darkred]
[/COLOR][/B]> **Qchan said:**
> **[COLOR=darkred]As for the original link, I'm not sure. I had a hard time finding it, so I honestly can't remember the original link. Sorry :/[/COLOR]**
I think I've found it:

[http://blog.adahsu.net/ada/space/start/2006-07-31/2](http://blog.adahsu.net/ada/space/start/2006-07-31/2)

or through Google Translate:

[http://74.125.91.132/translate_c?hl=en&sl=zh-TW&u=http://blog.adahsu.net/ada/space/start/2006-07-31/2&prev=/search%3Fq%3Dass2srt%26hl%3Den%26client%3Dfirefox-a%26channel%3Ds%26rls%3Dorg.mozilla:en-US:official%26sa%3DG&rurl=translate.google.ca&usg=ALkJrhgVBN4kHOjGPTOOiZr1Mh6TFCBNJQ](http://74.125.91.132/translate_c?hl=en&sl=zh-TW&u=http://blog.adahsu.net/ada/space/start/2006-07-31/2&prev=/search%3Fq%3Dass2srt%26hl%3Den%26client%3Dfirefox-a%26channel%3Ds%26rls%3Dorg.mozilla:en-US:official%26sa%3DG&rurl=translate.google.ca&usg=ALkJrhgVBN4kHOjGPTOOiZr1Mh6TFCBNJQ)

Hope this is useful to someone.

J-S

P.S. Seems the board censors a_s_s to ***, so if you try to download the attachment and it offers a file called ***2srt.pl.txt, just rename it to you know what. Sheesh...

---

### Post by SarahKH on 2010-04-13
Hmm I've been looking at the original of this script (as well as the modified version) and feeding it a utf8 *** taken from an Anime called Kiddy-game (ep2, ANBU release for those wondering).  As part of a 'format shift to m4v' script with HandBrake. 

Seems the script can get it wrong with the timing although I'm unsure how to fix it.  Jumbler outputs what appears to be the correct timestamps in to the srt. 

Attached the three files for poking at.

---

### Post by p014k on 2011-01-29
> **Qchan said:**
> [B][COLOR=darkred]
Sure, there are many programs that can do this, but they are mostly all GUI based. I know a lot of people have been looking for something they can use on the command line. I finally found the script and figured I'd share it with people.

It's under the GNU license, but just happened to be in Chinese. I translated it using Google's translator. I checked the code and everything works out pretty well.

If you have any problems with it, let me know. I have the original Chinese version.

As for the original link, I'm not sure. I had a hard time finding it, so I honestly can't remember the original link. Sorry :/
[/COLOR][/B]

[PHP]
#!/usr/bin/perl -w

use strict;

use encoding 'utf-8';

use Getopt::Long;

use File::Spec;



Getopt::Long::Configure( "pass_through", "no_ignore_case" );



# Default encoding
my $defaultEnc  = 'utf8';

my $fromEnc     = '';

my $toEnc       = '';

my $help        = 0;

my $preserve    = 0;

my $combine     = 0;

my $showVer     = 0;

my $showLicense = 0;

my $dosFormat   = 0;

my $macFormat   = 0;



my $oldTime = "";



$fromEnc = $ENV{'ASS2SRT_FROM'};

$toEnc   = $ENV{'ASS2SRT_TO'};



GetOptions(

    "help|h",     \$help,      "from|f=s",    \$fromEnc,

    "to|t=s",     \$toEnc,     "default|d=s", \$defaultEnc,

    "preserve|p", \$preserve,  "combine|c",   \$combine,

    "version|v",  \$showVer,   "dos|o",       \$dosFormat,

    "mac|m",      \$macFormat, "license|l",   \$showLicense

);



# Wrap format
my $crlf = "\n";



# If the specified output at the same time as Mac and DOS format, responding to an error message and the end of
( $dosFormat && $macFormat )

    && die( "\n&#37679;&#35492;: \n\t&#36984;&#38917; -m|--mac &#33287; -o|--dos &#19981;&#21487;&#21516;&#26178;&#23384;&#22312; \n" );



if ($dosFormat) { $crlf = "\r" . $crlf; }

if ($macFormat) { $crlf = "\r"; }



# Program version

my $version = "0.2.4.2";



# Display help message

if ($help) { usage(); }



# Show license information

if ($showLicense) { license(); }



# Show version of the message
if ($showVer) { showVersion(); }



# Source file encoding is not specified, the set with the same defaultEnc
if ( !$fromEnc ) { $fromEnc = $defaultEnc; }



# Do not specify the purpose of file encoding, the set with the same defaultEnc
if ( !$toEnc ) { $toEnc = $defaultEnc; }



#. *** file file name
my $assFile = shift || '';

if ( !$assFile ) { usage(); }



#. Srt file file name, the default value. *** file name, but changed the name extension. Srt

my $srtFile = shift || '';

if ( !$srtFile ) {

    $srtFile = $assFile;

    $srtFile =~ s|\.[^.]*$||;

    $srtFile .= ".srt";

}



# Using the parameters listed
print "Using parameters: \n";

print "\t .*** File Encoding: $fromEnc\n";

print "\t .SRT File Encoding: $toEnc\n";

print "\n";



# Open file
open( ASSFILE, "<", $assFile )

    or die 'Can not open ".***" the source file&#65306;' . $assFile . ", please check!&#65281;\n";

open( SRTFILE, ">", $srtFile )

    or die 'Can not open ".srt" The purpose of file&#65306;' . $srtFile . ", please check!\n";



# Specify the file encoding

binmode( ASSFILE, ':encoding(' . $fromEnc . ')' );



# Check the existence of the system environment variable OS (Windows should be)
my $OS_TYPE = $ENV{'OS'};



# Assigned to write the encoded file using the string set

my $toEncString = ':encoding(' . $toEnc . ')';



# Depending on OS type (only for Windows) file amendments to open coding

if ( $OS_TYPE && $OS_TYPE =~ m/windows/i ) {

    print "Operation System is: " . $OS_TYPE

        . ", Checking File Encoding... \n";



    # Only use UTF16 or UCS format when otherwise specified (other test)

    if ( ( $toEnc =~ m/utf16/i ) || ( $toEnc =~ m/ucs/i ) ) {

        $toEncString = ':raw' . $toEncString;

    }

}



# Specified file used to write code

binmode( SRTFILE, $toEncString );



# Windows on Unicode output file identification mark to join the BOM

if ( $toEncString =~ m/:raw/i ) {

    print SRTFILE "\x{FEFF}";

    print "Using unicode encoding, print BOM signature to file: " . $srtFile

        . "\n\n";

}



# Number of records subtitles

my $line = 0;



# Read. *** and deal with the source file
while (<ASSFILE>) {

    chomp;



    # If Dialougue in the beginning, the setting for the subtitles
    if (m/^Dialogue:/) {

        $line = writeSrt( $line, $_ );



    # If the beginning Title or Original, the source for the subtitles
    }

    elsif (m/^(Title:|Original)/) {

        print $_ . "\n";

    }



}



# Close the file

close ASSFILE;

close SRTFILE;



# Write. Srt file

sub writeSrt {



    # Deal with the number of rows

    my $line = $_[0];



    # From. *** of the original content

    my $content = $_[1];



    my $begin;

    my $end;

    my $subtitle;

    my $currentTime;



    # Solved starting time, ending time, subtitle format, subtitles content

    if ( $content

        =~ m/Dialogue: [^,]*,([^,]*),([^,]*),([^,]*),[^,]*,[^,]*,[^,]*,[^,]*,[^,]*,(.*)$/

        )

    {

        $begin    = $1;

        $end      = $2;

        $subtitle = $4;



        my $isComment = $3;



        # the separator between seconds and ms is "," -- not ".", so we change it !

        $begin =~ s/\./\,/g;

        $end   =~ s/\./\,/g;



        # If the time format will not be part of the hour when the two yards, make up two yards
        if ( $begin =~ m/^\d{1}:/ ) {

            $begin = "0" . $begin;

        }



        if ( $end =~ m/^\d{1}:/ ) {

            $end = "0" . $end;

        }



        # First filter out the end of every title to the digital sign in order to follow-up to the output under a variety of formats on different platforms

        $subtitle =~ s/\r$//g;



        # If there is no such setting. *** control commands, then filter out the

        if ( !$preserve ) {

            $subtitle =~ s/\{\\[^}]*\}//g;

        }



        # Comment if the subtitle format, then in the before and after the add ()
        if ( $isComment eq 'comment' ) {

            $subtitle = '(' . $subtitle . ')';

        }



        # Write. Srt file
         # Because. *** unit of time (10ms) with. Srt (1ms), so the full complement of 0
        $currentTime = $begin . "0 --> " . $end . "0";



        $subtitle =~ s/\\N/$crlf/g;



        # Timeline combined output mode
        if ($combine) {



            if ( $oldTime eq $currentTime ) {

                print SRTFILE $subtitle;

            }

            else {

                $line++;

                if ( $line > 0 ) {

                    print SRTFILE $crlf . $crlf . $crlf . $line . $crlf;

                }

                else {

                    print SRTFILE $line . $crlf;

                }

                print SRTFILE $currentTime . $crlf;

                print SRTFILE $subtitle;

            }

            $oldTime = $currentTime;

        }

        else {

            # The general output model

            $line++;

            print SRTFILE $line . $crlf;

            print SRTFILE $currentTime . $crlf;

            print SRTFILE "$subtitle " . $crlf . $crlf . $crlf;

        }



        return $line;

    }

}



# Use

sub usage {

    print <<__HELP__;



ass2srt [option] .*** source files [.srt purpose of file]



    The Advanced SubStation Alpha ".***" file format to SubRip ".srt" format. 



Options:
  -h --help               help show this help message

    

  -d, --default=encoding  default = encoding set the default file encoding, which is the purpose of the source file and use the same code file.

                          The default value is UTF-8 encoding format.
                                     

  -f, --from=encoding    from = encoding specified source file. *** coding system used. The set will be covered by the aforementioned pre -
                           Coding based on the settings file, when not specified the default file encoding for the default value.
                        &#8251; You can also use the system environment variables specified ASS2SRT_FROM
                                

  -t, --to=encoding       encoding file specified purposes. srt coding system used. The set will be covered by the aforementioned pre -
                           Coding based on the settings file, when not specified the default file encoding for the default value.
                        &#8251; You can also use the system environment variables specified ASS2SRT_TO



  -p, --preserve          preserve the source file to retain. *** subtitles in the control instructions, write together. srt file.


  -c, --combine              combine the same number of merge subtitles timeline set by the content under a single timeline.
  

  -o, --dos               dos specified output file format for DOS (the default format for Unix)
                        &#8251; At the same time can not be set -m/--mac
  

  -m, --mac               mac specify the output file format for the Mac (the default format for Unix)
                        &#8251; At the same time can not be set -o/--dos


.*** source file:

    &#31526;&#21512; Advanced SubStation Alpha (.***) &#25110; SubStation Alpha (.ssa) &#26684;&#24335;

    Subtitles of the original file.


[.srt purpose file]&#65306;

   SubRip default output file format for the purpose of file name, the default value. *** the same source file,

     However, extension changed to. Srt.


Operation Example:



 1. Unicode/UTF-16 LE will be encoded. *** into the source file to Big5 encoding. Srt purpose file

  

       myhost \ $ perl ass2srt.pl-f utf16-le-t big5 utf16-le.*** big5.srt

      

   2. Big5 encoding. *** into the source file to UTF-8 encoded. Srt purpose file

    

       myhost \ $ perl ass2srt.pl-f big5-t utf8 big5.*** utf8.srt

      

   3. To be UTF-8 encoded. *** into the source file to UTF-8 encoded. Srt purpose file

  

       myhost \ $ perl ass2srt.pl utf-8.*** utf-8.srt

      

   4. UCS-2LE encoding. *** source file into the UCS-2LE encoding. Srt purpose file

  

       myhost \ $ perl ass2srt.pl-f ucs-2le-t ucs-2le ucs-2le.*** ucs-2le.srt

      

   5. Through the environment variables specified encoding type

      &#8251; Do not some of the operating system settings before and after the words "or 'quotation marks
  

     myhost \ $ export ASS2SRT_FROM = utf16-le

       myhost \ $ export ASS2SRT_TO = big5

       myhost \ $ perl ass2srt.pl utf16-le.*** big5.srt                              



__HELP__

    exit 2;

}



# Show version of the message

sub showVersion {



    print <<__VERSION__;



ass2srt $version - Convert subtitles from .*** to .srt format

    

  Advanced SubStation Alpha subtitle file format conversion tool

  (c) 2006 Ada Hsu, hungwei.hsu (at) gmail (dot) com



__VERSION__

    exit 2;

}



# &#36575;&#39636;&#25480;&#27402;

sub license {



    print <<__LICENSE__;



  ass2srt $version - Convert subtitles from .*** to .srt format



  Advanced SubStation Alpha subtitle file format conversion tool

  (c) 2006 Ada Hsu, hungwei.hsu (at) gmail (dot) com

  

 The use of the software CC-GNU GPL (http://creativecommons.org/licenses/GPL/2.0/) authorization,

   You can view the relevant provisions of http://www.gnu.org/copyleft/gpl.html text.

  

   You are free to use the software, but software maintenance personnel will not use the software created by the software and hardware

   Physical injury or loss of any responsibility.


__LICENSE__

    exit 2;



}
[/PHP]
For some reason I can't get this working. I copy/pasted the code into a script.pl file. In the terminal I try to do perl script.pl -h for the help, but it gives me this;

Global symbol "$perl" requires explicit package name at script.pl line 439.
Global symbol "$perl" requires explicit package name at script.pl line 439.
Global symbol "$perl" requires explicit package name at script.pl line 439.
Global symbol "$perl" requires explicit package name at script.pl line 439.
Global symbol "$export" requires explicit package name at script.pl line 439.
Global symbol "$export" requires explicit package name at script.pl line 439.
Global symbol "$perl" requires explicit package name at script.pl line 439.
Execution of script.pl aborted due to compilation errors.

Line 439 is;

    print <<__HELP__;

What is wrong here?

---

### Post by Qchan on 2011-01-29
> **p014k said:**
> For some reason I can't get this working. I copy/pasted the code into a script.pl file. In the terminal I try to do perl script.pl -h for the help, but it gives me this;

Global symbol "$perl" requires explicit package name at script.pl line 439.
Global symbol "$perl" requires explicit package name at script.pl line 439.
Global symbol "$perl" requires explicit package name at script.pl line 439.
Global symbol "$perl" requires explicit package name at script.pl line 439.
Global symbol "$export" requires explicit package name at script.pl line 439.
Global symbol "$export" requires explicit package name at script.pl line 439.
Global symbol "$perl" requires explicit package name at script.pl line 439.
Execution of script.pl aborted due to compilation errors.

Line 439 is;

    print <<__HELP__;

What is wrong here?


[b][color=darkred]
Try running like this:

> 
./script -h


Make sure it has executable rights.

I still use this script and it works still to this day. 


[/color][/b]

---

### Post by federal_topone on 2011-01-29
**thankyou for sharing.. i have same problem.**









[[COLOR=Lime]syahmei.blogspot.com[/COLOR]]("http://syahmei.blogspot.com")

---

### Post by Qchan on 2011-01-29
[PHP]#!/usr/bin/perl -w
use strict;
use warnings;
use encoding 'utf-8';
use Getopt::Long;
use File::Spec;

Getopt::Long::Configure( "pass_through", "no_ignore_case" );

# Default encoding
my $defaultEnc  = 'utf8';
my $fromEnc     = '';
my $toEnc       = '';
my $help        = 0;
my $preserve    = 0;
my $showVer     = 0;
my $showLicense = 0;
my $dosFormat   = 0;
my $macFormat   = 0;

my $oldTime = "";

$fromEnc = $ENV{'ASS2SRT_FROM'};
$toEnc   = $ENV{'ASS2SRT_TO'};

my $DEBUG = 0;
my $noCorrect = 0;

GetOptions(
    "help|h",     \$help,      "from|f=s",    \$fromEnc,
    "to|t=s",     \$toEnc,     "default|d=s", \$defaultEnc,
    "preserve|p", \$preserve,
    "version|v",  \$showVer,   "dos|o",       \$dosFormat,
    "mac|m",      \$macFormat, "license|l",   \$showLicense,
    "debug",      \$DEBUG,     "nocorrect",   \$noCorrect
);


# Lines read from .*** file will be put here (each in a hash with the
# relevant info) to be written to the .srt file after some post-processing.
my @lines;

# Wrap format
my $crlf = "\n";

# If the specified output at the same time as Mac and DOS format, responding to an error message and the end of
( $dosFormat && $macFormat )
    && die( "\n??: \n\t?? -m|--mac ? -o|--dos ?????? \n" );

if ($dosFormat) { $crlf = "\r" . $crlf; }
if ($macFormat) { $crlf = "\r"; }

# Program version
my $version = "0.3";

# Display help message
if ($help) { usage(); }

# Show license information
if ($showLicense) { license(); }

# Show version of the message
if ($showVer) { showVersion(); }

# Source file encoding is not specified, the set with the same defaultEnc
if ( !$fromEnc ) { $fromEnc = $defaultEnc; }

# Do not specify the purpose of file encoding, the set with the same defaultEnc
if ( !$toEnc ) { $toEnc = $defaultEnc; }

#. *** file file name
my $assFile = shift || '';
if ( !$assFile ) { usage(); }

#. Srt file file name, the default value. *** file name, but changed the name extension. Srt
my $srtFile = shift || '';
if ( !$srtFile ) {
    $srtFile = $assFile;
    $srtFile =~ s|.[^.]*$||;
    $srtFile .= ".srt";
}

# Using the parameters listed
print "Using parameters: \n";
print "\t .*** File Encoding: $fromEnc\n";
print "\t .SRT File Encoding: $toEnc\n";
print "\n";

# Open file
open( ASSFILE, "<", $assFile )
    or die 'Can not open ".***" the source file:' . $assFile . ", please check!!\n";

# Specify the file encoding
binmode( ASSFILE, ':encoding(' . $fromEnc . ')' );

# Check the existence of the system environment variable OS (Windows should be)
my $OS_TYPE = $ENV{'OS'};

# Assigned to write the encoded file using the string set
my $toEncString = ':encoding(' . $toEnc . ')';

# Depending on OS type (only for Windows) file amendments to open coding
if ( $OS_TYPE && $OS_TYPE =~ m/windows/i ) {
    print "Operation System is: " . $OS_TYPE
        . ", Checking File Encoding... \n";

    # Only use UTF16 or UCS format when otherwise specified (other test)
    if ( ( $toEnc =~ m/utf16/i ) || ( $toEnc =~ m/ucs/i ) ) {
        $toEncString = ':raw' . $toEncString;
    }
}

# Windows on Unicode output file identification mark to join the BOM
if ( $toEncString =~ m/:raw/i ) {
    print SRTFILE "\x{FEFF}";
    print "Using unicode encoding, print BOM signature to file: " . $srtFile
        . "\n\n";
}

# Number of records subtitles
my $lineNum = 0;

# Read. *** and deal with the source file
while (<ASSFILE>) {
    chomp;

    # If Dialougue in the beginning, the setting for the subtitles
    if (m/^Dialogue:/) {
        $lineNum = extractLine( $lineNum, $_ );

    # If the beginning Title or Original, the source for the subtitles
    }
    elsif (m/^(Title:|Original)/) {
        print $_ . " ";
    }

}

# Close the file
close ASSFILE;


# post-process lines to remove errors.
if (!$noCorrect)
{
    for (my $i = 0; $i < scalar @lines; $i++)
    {
        my $line = $lines[$i];
        my $prevLine = undef;
        $prevLine = $lines[$i-1] if $i > 0;

        # if the begin of the previous line is the same as the begin of this line,
        # merge the two lines.
        if ($prevLine && $prevLine->{begin} eq $line->{begin})
        {
            # merge subtitles
            $prevLine->{subtitle} .= " " . $line->{subtitle};

            # remove line $i from the list
            @lines = (@lines[0..$i-1], @lines[$i+1..$#lines]);

            # resync things for next test
            $i--;
            $prevLine = undef;
            $prevLine = $lines[$i-1] if $i > 0;
        }

        # if the end of the previous line is smaller than the begin of this line,
        # change the end of the previous line to be the begin of this line.
        if ($prevLine && $prevLine->{end} gt $line->{begin})
        {
            $prevLine->{end} = $line->{begin};
        }
    }
}


open( SRTFILE, ">", $srtFile )
    or die 'Can not open ".srt" The purpose of file:' . $srtFile . ", please check!\n";

# Specified file used to write code
binmode( SRTFILE, $toEncString );

# Write SRT file.
my $lineNumber = 1;
foreach my $line (@lines)
{
    # Write. Srt file
    # Because. *** unit of time (10ms) with. Srt (1ms), so the full complement of 0
    my $currentTime = $line->{begin} . "0 --> " . $line->{end} . "0";

    print SRTFILE $lineNumber . $crlf;
    print SRTFILE $currentTime . $crlf;
    print SRTFILE $line->{subtitle} . " " . $crlf . $crlf;

    $lineNumber++;
}

close SRTFILE;


# Extract data for one line in the .*** file
sub extractLine {

    # Deal with the number of rows
    # From. *** of the original content
    my ($lineNumber, $content) = @_;

    my $begin;
    my $end;
    my $subtitle;
    my $currentTime;

    # Solved starting time, ending time, subtitle format, subtitles content
    if ( $content
        =~ m/Dialogue: [^,]*,([^,]*),([^,]*),([^,]*),[^,]*,[^,]*,[^,]*,[^,]*,[^,]*,(.*)$/
        )
    {
        $begin    = $1;
        $end      = $2;
        $subtitle = $4;

        my $isComment = $3;

        print "\nLine: $lineNumber\n  Begin: [$begin]  End: [$end]  isComment: [$isComment]\n  Subtitle: [$subtitle]\n"
            if $DEBUG;

        # the separator between seconds and ms is "," -- not ".", so we change it !
        $begin =~ s/\./,/g;
        $end   =~ s/\./,/g;

        # If the time format will not be part of the hour when the two yards, make up two yards
        if ( $begin =~ m/^\d{1}:/ ) {
            $begin = "0" . $begin;
        }

        if ( $end =~ m/^\d{1}:/ ) {
            $end = "0" . $end;
        }

        # First filter out the end of every title to the digital sign in order to follow-up to the output under a variety of formats on different platforms
        #$subtitle =~ s/r$//g;

        # If there is no such setting. *** control commands, then filter out the
        if ( !$preserve ) {
            $subtitle =~ s/{[^}]*}//g;
        }

        # Comment if the subtitle format, then in the before and after the add ()
        if ( $isComment eq 'comment' ) {
            $subtitle = '(' . $subtitle . ')';
        }

        print "\nAfter:\n  Begin: [$begin]  End: [$end]  isComment: [$isComment]\n  Subtitle: [$subtitle]\n"
            if $DEBUG;

        my %line = ( begin => $begin, end => $end, isComment => $isComment, subtitle => $subtitle );
        push @lines, \%line;

        return $lineNumber;
    }
}

# Use
sub usage {
    print <<__HELP__;

ass2srt [option] .*** source files [.srt purpose of file]

    The Advanced SubStation Alpha ".***" file format to SubRip ".srt" format.

Options:
  -h --help               help show this help message

  -d, --default=encoding  default = encoding set the default file encoding, which is the purpose of the source file and use the same code file.
                          The default value is UTF-8 encoding format.

  -f, --from=encoding    from = encoding specified source file. *** coding system used. The set will be covered by the aforementioned pre -
                           Coding based on the settings file, when not specified the default file encoding for the default value.
                        &#8251; You can also use the system environment variables specified ASS2SRT_FROM

  -t, --to=encoding       encoding file specified purposes. srt coding system used. The set will be covered by the aforementioned pre -
                           Coding based on the settings file, when not specified the default file encoding for the default value.
                        &#8251; You can also use the system environment variables specified ASS2SRT_TO

  -p, --preserve          preserve the source file to retain. *** subtitles in the control instructions, write together. srt file.

  -o, --dos               dos specified output file format for DOS (the default format for Unix)
                        &#8251; At the same time can not be set -m/--mac

  -m, --mac               mac specify the output file format for the Mac (the default format for Unix)
                        &#8251; At the same time can not be set -o/--dos

  --debug                 print debugging output for each line of the .*** file read.

  --nocorrect             don't attempt to correct errors in subtitles
                        if not specified, corrections will be made for the following errors:
                          - subtitle i+1 begins before subtitle i ends - subtitle i's end will be set to subtitle i+1's begin
                          - subtitle i+1 begins at the same time as subtitle i begins - subtitles will be merged into one subtitle

.*** source file:
    &#31526;? Advanced SubStation Alpha (.***) ? SubStation Alpha (.ssa) ??
    Subtitles of the original file.

[.srt purpose file]&#65306;
   SubRip default output file format for the purpose of file name, the default value. *** the same source file,
     However, extension changed to. Srt.

Operation Example:

 1. Unicode/UTF-16 LE will be encoded. *** into the source file to Big5 encoding. Srt purpose file

       myhost  \$ perl ass2srt.pl-f utf16-le-t big5 utf16-le.*** big5.srt

   2. Big5 encoding. *** into the source file to UTF-8 encoded. Srt purpose file

       myhost  \$ perl ass2srt.pl-f big5-t utf8 big5.*** utf8.srt

   3. To be UTF-8 encoded. *** into the source file to UTF-8 encoded. Srt purpose file

       myhost  \$ perl ass2srt.pl utf-8.*** utf-8.srt

   4. UCS-2LE encoding. *** source file into the UCS-2LE encoding. Srt purpose file

       myhost  \$ perl ass2srt.pl-f ucs-2le-t ucs-2le ucs-2le.*** ucs-2le.srt

   5. Through the environment variables specified encoding type
      &#8251; Do not some of the operating system settings before and after the words "or 'quotation marks

     myhost  \$ export ASS2SRT_FROM = utf16-le
       myhost  \$ export ASS2SRT_TO = big5
       myhost  \$ perl ass2srt.pl utf16-le.*** big5.srt

__HELP__
    exit 2;
}

# Show version of the message
sub showVersion {

    print <<__VERSION__;

ass2srt $version - Convert subtitles from .*** to .srt format

  Advanced SubStation Alpha subtitle file format conversion tool
  (c) 2006 Ada Hsu, hungwei.hsu (at) gmail (dot) com
  (c) 2009 Jean-Sebastien Guay, jean_seb (at) videotron (dot) ca

__VERSION__
    exit 2;
}

# ????
sub license {

    print <<__LICENSE__;

  ass2srt $version - Convert subtitles from .*** to .srt format

  Advanced SubStation Alpha subtitle file format conversion tool
  (c) 2006 Ada Hsu, hungwei.hsu (at) gmail (dot) com
  (c) 2009 Jean-Sebastien Guay, jean_seb (at) videotron (dot) ca

 The use of the software CC-GNU GPL (http://creativecommons.org/licenses/GPL/2.0/) authorization,
   You can view the relevant provisions of http://www.gnu.org/copyleft/gpl.html text.

   You are free to use the software, but software maintenance personnel will not use the software created by the software and hardware
   Physical injury or loss of any responsibility.

__LICENSE__
    exit 2;

}[/PHP]

[b][color=darkred]
Try this script.
[/b][/color]

---

