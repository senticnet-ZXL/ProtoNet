# ProtoNet
ProtoNet is a scalable and versatile knowledge base that effectively represents both commonsense and real-world knowledge, supporting robust commonsense reasoning and inference.

## Functions
In protonet_graph.py, we define over 20 functions to explore ProtoNet.

We show the examples of using these functions:
```
protonet = read_json_file("protonet_fact_v3.json")
graph = Graph(protonet)

# generate all nodes and edges in ProtoNet:
graph.nodes()
graph.edges()

graph.get_number_of_nodes()
# output: 1409185
graph.get_number_of_edges()
# output: 3056776
graph.density()
# output: 3.0786328229340862e-06

graph.what_is("hammer")
# output: hammer --isA--> hand_tool
graph.get_node_degree("hammer")
# output: 24
graph.explain(node="hammer",relation="isA")
# output: hammer --isA--> hand_tool --isA--> tool
graph.what_can_be("hammer")
# output: [['isA', 'hand_tool'], ['isA', 'industrial_equipment'], ['isA', 'power_tool'], ['isA', 'tool'], ['mannerOf', 'beat'], ['usedFor', 'hit'], ['madeOf', 'forged_metal'], ['partOf', 'gunlock'], ['partOf', 'piano_action'], ['IntentionOf', 'build'], ['IntentionOf', 'demo'], ['Afford', 'breaking_glass'], ['Afford', 'break_glass'], ['Afford', 'nail_board'], ['Afford', 'break_wall'], ['Afford', 'break_window'], ['Afford', 'strike_nail'], ['Afford', 'force_nail_into_board'], ['Afford', 'break_fragile_objects'], ['Afford', 'nail_nails'], ['Afford', 'strike_with_great_force'], ['Afford', 'nail_nail'], ['Afford', 'hit_nail'], ['Afford', 'drive_in_nails']]
graph.generalize("hammer")
# output: [('Afford', 'BREAKING_GLASS'), ('mannerOf', 'STRIKE'), ('usedFor', 'HIT'), ('IntentionOf', 'BUILD'), ('isA', 'TOOL'), ('partOf', 'ARSENAL'), ('madeOf', 'FORGED_METAL')]

graph.relation_exist(node="hammer",relation="Afford")
# output: True
graph.relation_types("hammer")
# output: ['madeOf', 'Afford', 'IntentionOf', 'usedFor', 'partOf', 'mannerOf', 'isA']

graph.get_node_with_relation(node="hammer",relation="isA")
# output: 'hand_tool'
graph.get_node_with_relation(node="hammer",relation="usedFor")
# output: 'hit'
graph.find_last_nodes("hit_nail")
# output: ['hammer-->Afford-->hit_nail']
graph.get_all_node_with_relation(node="hammer",relation="Afford")
# output: ['breaking_glass', 'break_glass', 'nail_board', 'break_wall', 'break_window', 'strike_nail', 'force_nail_into_board', 'break_fragile_objects', 'nail_nails', 'strike_with_great_force', 'nail_nail', 'hit_nail', 'drive_in_nails']

graph.find_path(start_node="hammer",end_node="tool")
# output: [('START', 'hammer'), ('isA', 'hand_tool'), ('isA', 'tool')]
graph.find_all_paths(start_vertex="hammer",end_vertex="tool")
# output: [[('START', 'hammer'), ('isA', 'hand_tool'), ('isA', 'tool')], [('START', 'hammer'), ('isA', 'power_tool'), ('isA', 'tool')], 002: [('START', 'hammer'), ('isA', 'tool')], [('START', 'hammer'), ('mannerOf', 'beat'), ('isA', 'band'), ('isA', 'record'), ('isA', 'tool')]...]
graph.get_path(start_node="hammer",end_node="tool")
# output:'hammer --isA--> hand_tool --isA--> tool'

graph.get_similarity(node1="hammer",node2="pen",relation="Afford")
# output: 0.11111
graph.get_similarity(node1="hammer",node2="brick",relation="Afford")
# output: 0.66667

graph.add_node("a_new_node")
graph.add_edge(("a_new_node", "isA","testing_example"))
```


