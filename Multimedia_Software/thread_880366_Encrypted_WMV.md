---
title: "Encrypted WMV"
date: 2008-08-04
forum: Multimedia Software
---

### Post by RealG187 on 2008-08-04
Okay I found this:

[http://epl.lib.overdrive.com/70D36C92-38C7-435F-8609-BAF4C3851647/10/324/en/ContentDetails.htm?ID=54F85C31-7B28-4A52-87BE-273E62B003A6](http://epl.lib.overdrive.com/70D36C92-38C7-435F-8609-BAF4C3851647/10/324/en/ContentDetails.htm?ID=54F85C31-7B28-4A52-87BE-273E62B003A6)


It appers to be DRMed.

I want to play the video in Linux, but they dont make software for Linux.

When I went there there was a download to a .odm file

> <?xml version="1.0"?>
<!DOCTYPE OverDriveMedia SYSTEM "http://www.overdrive.com/DTDs/OverDriveMedia.dtd">
<OverDriveMedia id="0DBFD89E-1723-48CE-B87E-4EFDCECB4420-40" ODMVersion="2.0.0.0" OMCVersion="2.1.0.0">
	<WMLicense>
		<AcquisitionUrl>http://ofs.contentreserve.com/GetWMVLicense.asp?AcquisitionID={c93afe79-2ced-4eb8-9526-6e08bd310a18}</AcquisitionUrl>
	</WMLicense>
<![CDATA[<Metadata>	<ContentType>Mobile Video</ContentType>	<Title>Beef (Mobile Version)</Title>	<SortTitle>Beef (Mobile Version)</SortTitle>	<Publisher>Image Entertainment</Publisher>	<ThumbnailUrl>http://images.contentreserve.com/ImageType-200/1096-1\{54F85C31-7B28-4A52-87BE-273E62B003A6}Img200.jpg</ThumbnailUrl>	<Creators>		<Creator role="Director" file-as="Spirer, Peter">Peter Spirer</Creator>		<Creator role="Performer" file-as="Cent, 50">50 Cent</Creator>		<Creator role="Performer" file-as="Jay-Z">Jay-Z</Creator>		<Creator role="Performer" file-as="Nas">Nas</Creator>		<Creator role="Performer" file-as="DMX">DMX</Creator>		<Creator role="Performer" file-as="Dog, Snoop">Snoop Dog</Creator>		<Creator role="Performer" file-as="Tupac">Tupac</Creator>		<Creator role="Performer" file-as="Dre, Dr.">Dr. Dre</Creator>		<Creator role="Performer" file-as="Cube, Ice">Ice Cube</Creator>		<Creator role="Performer" file-as="Rule, Ja">Ja Rule</Creator>		<Creator role="Performer" file-as="10, Mack">Mack 10</Creator>		<Creator role="Performer" file-as="Common">Common</Creator>		<Creator role="Performer" file-as="Hill, Cypress">Cypress Hill</Creator>		<Creator role="Performer" file-as="Simmons, Russell">Russell Simmons</Creator>		<Creator role="Performer" file-as="NWA">NWA</Creator>		<Creator role="Performer" file-as="KRS-One">KRS-One</Creator>		<Creator role="Performer" file-as="Chan, MC">MC Chan</Creator>		<Creator role="Performer" file-as="Dee, Kool Moe">Kool Moe Dee</Creator>		<Creator role="Performer" file-as="Bee, Busy">Busy Bee</Creator>		<Creator role="Performer" file-as="Rhames, Ving">Ving Rhames</Creator>		<Creator role="Performer" file-as="III, Quincy Jones">Quincy Jones III</Creator>	</Creators>	<Subjects>		<Subject id="56">Music</Subject>	</Subjects>	<Languages>		<Language code="en">English</Language>	</Languages><Description>The definitive look into the deep and harsh world of high profile beefs told by the artists themselves. The mc battle... Hip hop&#39;s war of words... Who&#39;s the illest on the mic... What happens when the raw energy of the inner city spills over from the studio to the streets. Today the stakes are high, and the consequences are becoming more and more real. What effect will this have on the future of hip hop? Judge for yourself! </Description></Metadata>]]>
	<DrmInfo>
		<PlayOnPC>1</PlayOnPC>
		<PlayOnPCCount>-1</PlayOnPCCount>
		<BurnToCD>0</BurnToCD>
		<BurnToCDCount>-1</BurnToCDCount>
		<PlayOnPM>1</PlayOnPM>
		<TransferToSDMI>1</TransferToSDMI>
		<TransferToNonSDMI>1</TransferToNonSDMI>
		<TransferCount>-1</TransferCount>
		<ExpirationDate>2008-08-07T03:16:16Z</ExpirationDate>
</DrmInfo>
	<Formats>
		<Format name="Medium Quality">
			<Quality level="Medium"/>
			<Protocols>
				<Protocol method="download" baseurl="http://wmv.contentreserve.com/WMVStore1"/>
			</Protocols>
			<Parts count="1">
				<Part number="1" filesize="430649738" name="Part 01" filename="1096-1\{0DBFD89E-1723-48CE-B87E-4EFDCECB4420}Fmt40-Part01.wmv" duration="102:55"/>
			</Parts>
		</Format>
	</Formats>
	<Source id="Edmonton">
		<Name>Edmonton Public Library</Name>
		<WebsiteUrl>http://epl.lib.overdrive.com</WebsiteUrl>
		<BannerUrl>http://epl.lib.overdrive.com/ODMBanner.gif</BannerUrl>
		<AccentColor>#eeeeee</AccentColor>
	</Source>
</OverDriveMedia>

From this:

<Formats>
		<Format name="Medium Quality">
			<Quality level="Medium"/>
			<Protocols>
				<Protocol method="download" baseurl="http://wmv.contentreserve.com/WMVStore1"/>
			</Protocols>
			<Parts count="1">
				<Part number="1" filesize="430649738" name="Part 01" filename="1096-1\{0DBFD89E-1723-48CE-B87E-4EFDCECB4420}Fmt40-Part01.wmv" duration="102:55"/>
			</Parts>
		</Format>
	</Formats>
I got the URL
[http://wmv.contentreserve.com/WMVStore1/1096-1%5C%7B54F85C31-7B28-4A52-87BE-273E62B003A6%7DFmt35-Part01.wmv](http://wmv.contentreserve.com/WMVStore1/1096-1%5C%7B54F85C31-7B28-4A52-87BE-273E62B003A6%7DFmt35-Part01.wmv)

So I downloaded the file but Totem media player says the file is encrypted and cannot be played. VLC shows scrambled things.

Is there a way to decrypt the file? There has to be a way to play it (afterall that is the point of having a video file). Does the ODM file have a key needed to play it? If so, how do I make it play?

This is why DRM sucks! :(

---

