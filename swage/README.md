# SWAGE
The **sw**ift L**ag**rangian to **E**ulerian (SWAGE) library is quit general and allows users to implement a large range of methods on unstructured arbitrary-order 3D meshes.  This library supports connectivity data structures and index spaces needed to implement low-order or high-order numerical methods.  SWAGE is designed to work with the elements library that contains e.g., quadrature sets, basis functions, Jacobian matrices, etc.  The SWAGE library has unique index spaces to support arbitrary-order Lagrangian material dynamic methods that solve the governing equations for motion on an arbitrary-order mesh that moves with the material.  The SWAGE library also allows code developers to create high-order Eulerian fluid-dynamic codes using high-order meshes that are conformal to a curved boundary (e.g., a wing). 

## Descriptions
The index spaces in SWAGE are:

* elements (the computational mesh is decomposed into non-overlapping elements)
* vertices (kinematic degrees of freedom for an element)
* nodes (a continuous space that coincides with the Lobatto point locations)
* gauss points (a discontinuous space that are the Lobatto point locations)
* sub-cells (a decomposition of an element using the nodes)
* sub-zones (a decomposition of an element using the vertices)
* surface (a surface of the element)
* patch (a portion of the surface that coincides with the surface of a sub-cell)
* facet (a portion of a patch)
* corner (a corner of a sub-cell)

Connectivity data structures exist to map from from an index to another index space (e.g., all nodes in an element) and to walk over neighboring mesh entities (e.g., all sub-cells around a sub-cell).  The SWAGE library is stitched together with the elements library in the geometry library.  

The index spaces for the mesh are denoted with a gid and the index spaces for local mesh entities are denoted with a lid.  For example, walking over all the sub-cells in the mesh and then all the nodes in the sub-cell would be, 
```
for (int cell_gid = 0; cell_gid < num_elem; cell_gid++) {
   // a loop over all the 
   for (int node_lid = 0; node_lid < 8; node_lid++){
      
   }
}
```