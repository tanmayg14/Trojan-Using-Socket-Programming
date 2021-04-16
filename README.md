# Trojan-Using-Socket-Programming

INTRODUCTION 

A Trojan horse is a program that contains or installs a malicious program (sometimes called the payload or ‘trojan’). The term is derived from the classical myth of the Trojan Horse. Trojan horses may appear to be useful or interesting programs (or at the very least harmless) to an unsuspecting user, but are actually harmful when executed.
There are two common types of Trojan horses. One, is otherwise useful software that has been corrupted by a cracker inserting malicious code that executes while the program is used. Examples include various implementations of weather alerting programs, computer clock setting software, and peer to peer file sharing utilities. The other type is a standalone program that masquerades as something else, like a game or image file, in order to trick the user into some misdirected complicity that is needed to carry out the program’s objectives.
This project report focuses on an interactive application through which we establish a server-client connection and attack the victim’s system through the established network to transfer, edit, replicate and download malicious files from server end to client end via socket programming . The application consists of two parts: server and client.
How a hacker establishes the connection to another user’s computer, is that the hacker running the “client” portion establishes a connection to the IP address of a known PC that has the “server” portion installed upon it. If the hacker running the “client” portion doesn’t know the IP address of the user’s PC which has been compromised by the “server” portion. The hacker usually initiates a series of connections to a large range of IP addresses on the Internet (known as “scanning”), looking for any PC that responds back to the attempt. If a PC responds back, it responds with its IP address. Then all the hacker has to do, is to establish a connection to that IP address.
We have taken the local address of the system in place of the IP address to show a prototype of the big picture. Because of this, both of the parts needs to be on the same network in order to establish the sever-client connection and run the program without any errors.
Now, let’s see how to code this file transfer in details.  
Libraries Used: 

1.	Socket Programming:- 

Sockets and the socket API are used to send messages across a network. They provide a form of inter-process communication(IPC) .It is a way of connecting two nodes on a network to communicate with each other. The network can be a logical, local network to the computer, or one that’s physically connected to an external network, with its own connections to other networks.here are two sets of verbs to use for communication. You can use send and recv, or you can transform your client socket into a file-like beast and use read and write.

2.	OS :- 

This module provides a portable way of using operating system dependent functionality. If you just want to read or write a file see open(), if you want to manipulate paths, see the os.path module, and if you want to read all the lines in all the files on the command line see the file input module.

3.	Shutil :- 

The shutil module offers a number of high-level operations on files and collections of files. In particular, functions are provided which support file copying and removal. For operations on individual files, see also the os module.

4.	Random:- 
    
Random module allows us to generate random integers in a given range. 
 
Assumptions 
The above program is executed on a single machine. Socket programming is meant for distributed programming. The same piece of code snippet when present on different machines which have web browsers installed can satisfy that requirement. This is just the bare bones service logic.  


Server End

●	First of all , we try to establish a connection from server end to the client and as   soon as the connection is established , a message is printed ‘address[0], "took the bait"’.  
●	Here address[0] is a python list with the index informing the attacker the IP address of the victim.
●	Now , as we established the connection , we plant the trojan and use respective functions   to transfer files in various ways.   


Client End

●	The client takes the bait from the server end. 
●	Changes are made with respect to the functions called at the server end. 
●	After the execution of any function, a message is printed at the client end signalling that the file transfer has taken place successfully .
 


     	Implementation

Now, let's have a look at the functionality of our program and exactly what changes the 
functions are implementing and how these changes are being made.

Establishing the connection:-

The server tries to establish the connection by the following piece of code and prints the message shown when the same is established.

  		Functions:-

●	Replace :- 

The replace function allows us to replace two files on the client end. Firstly, the location of the file to be replaced is entered and then the location of the file to be replaced with is entered. The data of the first file is erased then the data of the second file is copied into the first file and the function is completed. 
●	VCD :- 
VCD function prints us the current directory of the client’s end as shown below. We have attached both outputs at server’s and client’s end respectively. 

 
 

●	VFCD :- 
VFCD functions prints the number of files stored in a given directory. So we pass a directory at the server end and it calculates the number of files located in that directory and further prints them.

 
 

●	Download File ( download_file ) :- 
A copy of the file at the client end is downloaded in the server end. Firstly, the download_file function requires the name of the file with its directory at the client end, this file creates a copy of itself. Now the name of the new file to be created is passed and a file with the given name is downloaded at the server end. The new file is downloaded in the specified path with the same data as that of the file at the client end. 

. 
 

Now we can see that the data of the first file is transferred into the new file which is created at the server end.. 
●	Upload File ( upload ) :-
Upload function uploads certain files from the server end to the client end. The upload function requires the name of the file to be uploaded from the servers end with its directory. This file is further installed on the specified path of the client end with the file name “antiVirus1.py”. The file is cleverly named so to avoid any suspicion and will easily be ignored by the user on the client end.
  

●	Replicate :-
When this function is called , a special function known as ‘baby()’ is called which takes in it’s argument a location or a path. We have defined baby() such that it takes many paths at once and creates a python while checking each path for it’s existence as shown in try and throw block.

 

Then it starts replicating the file at all the mentioned paths with a random function generator which provides names to files being made. Then it makes a recursive call to each location in the list thus infecting each and every folder such as the branches of the tree. At the client end, the baby() function is simply provided with an address to initiate its implementation.



●	Exit :-
The exit function closes the socket via s.close(). The exit function is necessary because the while condition will keep in running.
 
 
