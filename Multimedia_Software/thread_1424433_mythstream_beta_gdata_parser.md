---
title: "mythstream beta gdata parser"
date: 2010-03-07
forum: Multimedia Software
---

### Post by sr_guy on 2010-03-07
Hi all,

I've been in contact with the author of mythstream:

[http://home.kabelfoon.nl/~moongies/streamtuned.html](http://home.kabelfoon.nl/~moongies/streamtuned.html)

We discussed pulling youtube playlists with gdata rss link, like:

[http://gdata.youtube.com/feeds/api/playlists/D1D291417488B8CC?max-results=50]("http://gdata.youtube.com/feeds/api/playlists/D1D291417488B8CC?max-results=50")

But I've found another way to breakup large playlists of 50+ items with this example:

[http://gdata.youtube.com/feeds/api/playlists/D1D291417488B8CC?&start-index=1&max-results=50]("http://gdata.youtube.com/feeds/api/playlists/D1D291417488B8CC?&start-index=1&max-results=50")

start-index=1 tells gdata to start at item 1 in the playlist
max-results=50 parses 50 items from the play list

Now the author of mythstream wrote a gdata parser and emailed it to me. It parses with the first example, but not parse with the example with the start-index=1 option. Is there anyone up to the challenge of writing a patch to be able to use the start-index option? Below you will find the gdata parser code:

```

#! /usr/bin/perl
# * ============================================================
# * File        : gdata feed reader
# * Release     : 1
# * Author      : Eric
# * Date        : 2010 mar
# * Description : gdate xml feed reader
# * Example     : http://gdata.youtube.com/feeds/base/playlists/2A293402C082840B?max-results=50
# * ============================================================
#

use English;
use XML::DOM;
use Data::Dumper;

$xml = new XML::DOM::Parser;

my $doc = XML::DOM::Document->new;
my $head = $doc->createXMLDecl ('1.0');
my $root = $doc->createElement('items');

sub specialchars
{
   local $str = shift;
   $str =~ s/&quot;/"/g;
   $str =~ s/&amp;/&/g;

   return $str;
}

sub newNode
{
  local $name  = shift;
  local $value = shift;
  local $node = $doc->createElement($name);
  local $text = $doc->createTextNode($value);
  $node->appendChild($text);
 
  return $node;
}

sub checkNode
{
   local $node = shift;   
   return ( $node && !($node =~ /^HASH/) )  # deref empty hash element
}

sub addMetaNode
{
  local $node  = shift;
  local $name  = shift;
  local $type  = shift;
 
  if ( checkNode($node) )
  {
   if ($type eq '')
   {
     $type = "inline";
     if ($node =~ /\n/)           { $type = "text" }
     if ($node =~ /<.+>.+<\/.+>/) { $type = "html" }
   }
   
   $meta = $doc->createElement('meta');
   $meta->appendChild( newNode('name'   , $name) );
   $meta->appendChild( newNode('content', $node) );
   $meta->appendChild( newNode('viewer' , $type) );
   $item->appendChild( $meta );
  }
}

sub parseItem
{
  local $entry = shift;
 
  # print Dumper($entry);

    $url   = $entry->getElementsByTagName("link")->item(0)->getAttribute("href");
    $descr = $entry->getElementsByTagName("content")->item(0)->getFirstChild->toString;
    $name  = $entry->getElementsByTagName("title")->item(0)->getFirstChild->toString;

    $name = specialchars($name);
    $descr = specialchars($descr);
   
    $item = $doc->createElement('item');
    $item->appendChild( newNode('name'   , $name));
    $item->appendChild( newNode('url'   , $url));
    $item->appendChild( newNode('handler'   , "youtube/vid_p"));
    $item->appendChild( newNode('descr'   , "see description item below") );
   
    $root->appendChild($item);

    addMetaNode($descr, 'description', 'html');
}

#------------------------------------------------------------------------------
# Init and Run
#------------------------------------------------------------------------------

&read_parse();    # get commandline parameters into @in
$source = $in[0]; # source filename from command line

eval{ $data = $xml->parsefile($source); };

$entries = $data->getElementsByTagName("entry");

$n = $entries->getLength;

for(my $i=0; $i<$n; $i++)
{
   parseItem($entries->item($i));
}

binmode STDOUT, ":utf8";

print $head->toString;
print $root->toString;
print "\n";

#--------------------------------------------------------------------------------
# get command line parameters
#--------------------------------------------------------------------------------

sub read_parse {
  local (*in) = @_ if @_;
  local ($i);
  push(@in, @ARGV);
  foreach $i (0 .. $#in) { $in[$i] =~ s/\+/ /g;}
  return scalar(@in);
}


```

---

