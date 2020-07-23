# AltGitLib
Parts Library for Altium in Git

## About
Unlike other shared libraries, this git repository holds not only the schematic symbols and PCB footprints, but also the library database.  This means there is no need for a live database connection to a central server.  You can simply clone this repo and begin using it offline.  Any additions or fixes you make can be committed to your fork. If you wish to contribute, please submit a pull-request and I'll merge it.

## Disclaimer
Use at your own risk.  Although I have used most of these parts on designs, I make no guarantee of accuracy of these part pinouts and footprints.  Please contribute fixes/improvements as a pull-request.

## Requirements
 - Altium Designer 16 or higher
 - MS Windows 7, 8, 10
 - MS Office 2010 or higher, 64-bit (if 32-bit version see: [additional requirements](https://www.altium.com/documentation/altium-designer/using-database-libraries-with-32-bit-and-64-bit-altium-design-software-on-the-same-computer) )
 - Git version control (and TortoiseGit is recommended)
 
## How to use
 - NOTE: There are some hard-coded file paths used in this library solution (please someone fix this).  If you clone this repository to ```C:\repos\AltGitLib``` then it should work out-of-the-box.  But if you clone it elsewhere you must edit the paths:
   - The file /PCB-Lib.DbLib references the file ```C:\repos\AltGitLib\dblink.udl```,
   - The file /dblink.udl references the folder ```C:\repos\AltGitLib\Libraries```,
   
 - See example project ```C:\repos\AltGitLib\Templates\PCB4Layer\PCB4Layer.PrjPcb\PCB4Layer.PrjPcb```
  - This example project references the library and contains an .OutJob which pulls data from it to create a Bill-Of-Materials document.
  
## Structure of this library
![altium-library-filestructure.png](doc/readme/altium-library-filestructure.png)

Names for schematic symbols, footprints, and library components should begin with the letter typically used as the beginning of the designator,  (There are some exceptions that I haven't cleaned-up.) i.e.:
 - Almost all resistors share the same schematic symbol named ```R```, stored in file of the same name: ```Symbols\R.Schlib```
 - Almost all surface-mount resistors with the size of 0603 share the same footprint named SM_IPC_R_0603, stored in a file of the same name: ```Footprints\SM_IPC_R_0603.PcbLib```
 - Each unique resistor component (i.e. with a unique orderable part#) should have it's own entry in the database.  The database part# for indexing is not the manufacturer's part#, since there can be alternate parts listed for a given component.  The database part# is typically descriptive and unique, i.e. ```R_10k_5%_0402```

From [Altium Documentation:](https://www.altium.com/documentation/altium-designer/working-with-database-libraries-ad)
One important thing to note when adding files to the repository, is that each symbol and model must be stored in its own library file. In a regular library - which can hold any number of symbols/models - changing a single entry would result in all being marked by the version control system as having been modified. Having one symbol/model per library file plays to the nature of version control, allowing you to keep track of exactly what has been modified and what has not.
