# Neo4j-Database-Design and Querying with Cypher

## Setup Steps

### Prerequisites
- Ensure you have Neo4j installed on your machine. You can download it from [Neo4j Download Center](https://neo4j.com/download-center/).
- Make sure you have the `players.csv` file containing the dataset. This file should be placed in the `import` directory of your Neo4j database.

### Step 1: Start Neo4j
1. Open Neo4j Desktop or start the Neo4j server if using the community edition.
2. Create a new project and a new graph database.
3. Start the database.

### Step 2: Access Neo4j Browser
1. Open Neo4j Browser by navigating to `http://localhost:7474` in your web browser.
2. Log in using the default credentials (`neo4j` / `neo4j`). You will be prompted to change the password.

### Step 3: Load the Dataset
1. Open the `Cypher Code.txt` file provided.
2. Copy the code for loading the dataset from the file.
3. Paste the code into the Neo4j Browser and run it to create nodes and relationships from the `players.csv` file.

### Step 4: Execute Cypher Queries
1. Copy the Cypher queries provided in the `Cypher Code.txt` file.
2. Paste the desired query into the Neo4j Browser and run it to retrieve the information from the graph database.

### Step 5: Explore and Customize
1. Modify the Cypher queries as needed to suit your analysis requirements.
2. Explore the data and visualize the graph using the Neo4j Browser tools.

### Example: Loading Players Data & ETL
```cypher
// Create Player Nodes with segregated D.O.B
LOAD CSV WITH HEADERS FROM 'file:///players.csv' AS row
MERGE (p:Player {id: row.`Player id`})
SET p.name = row.Player,
    p.position = row.Position,
    p.number = toInteger(row.Number),
    p.dob = row.`D.O.B`,
    p.day = toInteger(split(row.`D.O.B`, '.')[0]),
    p.month = toInteger(split(row.`D.O.B`, '.')[1]),
    p.year = toInteger(split(row.`D.O.B`, '.')[2]),
    p.age = toInteger(row.Age),
    p.height = toInteger(row.`Height (cm)`),
    p.caps = toInteger(row.Caps),
    p.internationalGoals = toInteger(row.`International goals`),
    p.playsInHomeCountry = row.`Plays in home country?`;

This README provides a comprehensive guide to setting up the Neo4j database and running the provided Cypher code, focusing on loading data and executing queries without including the actual Cypher code from the file.
