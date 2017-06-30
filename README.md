# Exile-Limited-Safe-SupplyBoxes
>Here you can Setup Limited Safes and Supplyboxes per Baselevel                              
>powered by HellBz
***

BaseLevel | Number of Safes | Number of Supply Boxes
------------ | ------------- | -------------
1 | 5 | 1
2 | 7 | 2
3 | 9 | 3
4 | 11 | 4
5 | 14 | 5
6 | 16 | 6
7 | 18 | 7
8 | 20 | 8
9 | 22 | 9
10 | 25 | 10


***


***                                                                                                             
 #### Mutch Thanks to:                                                                                            
 >   **110** --> For Inspiration and Testing                                                    
***
### INSTALLATION

This installation is not very Hard

#### Step 1
Update Your **exile.ini** from extDB

For ExtDB2 Users Add:
```c++
[getContainerSupplyBox]
SQL1_1 = SELECT id FROM container WHERE class = 'Exile_Container_SupplyBox' && territory_id = ?
Number of Inputs = 1
SQL1_INPUTS = 1
OUTPUT = 1
```  

And ExtDB3 Users only Add:
```c++
[getContainerSupplyBox]
SQL1_1 = SELECT id FROM container WHERE class = 'Exile_Container_SupplyBox' && territory_id = ?

SQL1_INPUTS = 1
OUTPUT = 1
```  

#### Step 2
Copy the Folder Overrides to you **Exile.YourMap** Folder

#### Step 3
in the **Config.cpp** in the ection **__CfgExileCustomCode__** you Add:
```c++
	ExileClient_util_world_canBuildHere                            = "overrides\ExileClient_util_world_canBuildHere.sqf";
	ExileServer_object_supplyBox_network_installSupplyBoxRequest   = "overrides\ExileServer_object_supplyBox_network_installSupplyBoxRequest.sqf";
```  

#### Step 4
in the **Config.cpp** in the ection **__CfgTerritories__** you Modify:

```c++
	prices[] = 
	{
		// Purchase Price 		Radius 		Number of Objects
		{5000,					15,			30 					}, // Level 1
		{10000,					30,			60 					}, // Level 2 
		{15000,					45,			90 					}, // Level 3
		{20000,					60,			120					}, // Level 4
		{25000,					75,			150					}, // Level 5
		{30000,					90,			180					}, // Level 6
		{35000,					105,		210					}, // Level 7
		{40000,					120,		240					}, // Level 8
		{45000,					135,		270					}, // Level 9
		{50000,					150,		300					}  // Level 10
	};
``` 

Change it to:

```c++
	prices[] = 
	{
		// Purchase Price 		Radius 		Number of Objects	Number of Safes		Number of Boxes
		{5000,                  15,         30,                 5,                  1               }, // Level 1
		{10000,                 30,         60,                 7,                  2               }, // Level 2 
		{15000,                 45,         90,                 9,                  3               }, // Level 3
		{20000,                 60,         120,                11,                 4               }, // Level 4
		{25000,                 75,         150,                14,                 5               }, // Level 5
		{30000,                 90,         180,                16,                 6               }, // Level 6
		{35000,                 105,        210,                18,                 7               }, // Level 7
		{40000,                 120,        240,                20,                 8               }, // Level 8
		{45000,                 135,        270,                22,                 9               }, // Level 9
		{50000,                 150,        300,                25,                 10              }  // Level 10
	};
``` 



#### Step 5 **(The BonusStep)**
This Step is for teh Action (Here User Can Delete a SupplyBox in own Territory)
in the **Config.cpp** in the ection **__CfgInteractionMenus-->SupplyBox-->Actions__** you Add:

```c++
			// Delete the SupplyBox.
			class Delete: ExileAbstractAction
			{
				title = "Delete SupplyBox";
				condition = "call ExileClient_util_world_isInOwnTerritory";
				action = "_this spawn ExileClient_object_container_pack";
			};
``` 

***  


Mutchas Gratias

And Have Fun with this Modification


Best Regards

**HellBz**
